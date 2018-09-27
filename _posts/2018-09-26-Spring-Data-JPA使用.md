---
layout:     post
title:      Spring Data JPA 使用探究
subtitle:   Spring Data JPA 使用探究
date:       2018-09-26
author:     HarlanSong
header-img: img/upload/aa97c67c8c1d79a0ce94c0fee2a30bfd8838df307da2f-RPC97X.jpg
catalog: true
tags:
    - Spring
    - JPA
    - Java
---

这里就滤过Spring Data JPA项目部署，不清楚的可以看一下开源项目[AutoAdmin](https://github.com/HarlanSong/AutoAdmin/tree/master/AutoAdmin-JPA)。

## Entity(表实体类)
一个表对应一个实体类，这里以**AutoAdmin**的sys_user表为例：

```java
import cn.songhaiqing.autoadmin.base.BaseEntity;
import org.hibernate.annotations.Where;
import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Table;


@Entity
@Table(name = "sys_user")
@Where(clause = "deleted=0")
public class SysUser extends BaseEntity {
    // 账号
    @Column(name = "account")
    private String account;
    // 密码
    @Column(name = "password")
    private String password;
    // 姓名
    @Column(name = "name")
    private String name;
    // 密码加密盐
    @Column(name = "salt")
    private String salt;

    public String getAccount() {
        return account;
    }

    public void setAccount(String account) {
        this.account = account;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSalt() {
        return salt;
    }

    public void setSalt(String salt) {
        this.salt = salt;
    }
}
```

**备注**

* @Table注解：写表名，如果表是刚好使用驼峰命名的话可以不写，建议写上。
* @Where ：查询该表时会自动加个的条件，用来做软删除过滤是非常好的选择，但是在@ManyToOne get该实体时如果数据已删除就会有问题，注意区别使用。
* @Column 字段申明，可以写在不同的位置，但个人习惯写在字段上一行。属性名可以和数据库表字段名不一样。


**BaseEntity**
实体类继承了BaseEntity，该类写一些通用的字段，像ID、创建时间、更新时间、删除标注等。

```java
import javax.persistence.*;
import java.util.Date;


@MappedSuperclass
public class BaseEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;

    @Column(name = "create_time", nullable = false,updatable = false)
    private Date createTime = new Date();

    @Column(name = "update_time", nullable = false)
    private Date updateTime = new Date();

    @Column(name = "deleted", nullable = false)
    private boolean deleted = false;

    public Date getCreateTime() {
        return createTime;
    }

    public Date getUpdateTime() {
        return updateTime;
    }

    public void setUpdateTime(Date updateTime) {
        this.updateTime = updateTime;
    }

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public void setCreateTime(Date createTime) {
        this.createTime = createTime;
    }

    public boolean isDeleted() {
        return deleted;
    }

    public void setDeleted(boolean deleted) {
        this.deleted = deleted;
    }
}
```

**备注**
* @Id @GeneratedValue(strategy = GenerationType.AUTO) ID 自增 
* 默认值：直接给变量设置初始值就可以了，create_time（创建时间）有点不一样，因为我不想以后改变值，因为需要设置updatable = false。

## Repository(表操作接口) 
有人习惯叫DAO或其他，JPA很重要的地方，使用JPA的语法简单直接的替代了大部分SQL。

**示例**
```java
import cn.songhaiqing.autoadmin.entity.SysUser;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.JpaSpecificationExecutor;
import org.springframework.stereotype.Repository;

@Repository
public interface SysUserRepository extends JpaRepository<SysUser, Long>,JpaSpecificationExecutor<SysUser> {
    SysUser findByAccount(String account);

    long countByAccount(String account);

    long countByAccountAndIdNot(String account, Long id);
}
```
 查询非常便利，详情参考下面语法：
 Keyword|Sample|JPQL snippet
---|---|---
And | findByLastnameAndFirstname | … where x.lastname = ?1 and x.firstname = ?2
Or | findByLastnameOrFirstname | … where x.lastname = ?1 or x.firstname = ?2
Is,Equals | findByFirstname,findByFirstnameIs,findByFirstnameEquals|… where x.firstname = ?1
Between | findByStartDateBetween | … where x.startDate between ?1 and ?2
LessThan | findByAgeLessThan | … where x.age < ?1
LessThanEqual | findByAgeLessThanEqual | … where x.age <= ?1
GreaterThan | findByAgeGreaterThan | … where x.age > ?1
GreaterThanEqual | findByAgeGreaterThanEqual | … where x.age >= ?1
After | findByStartDateAfter | … where x.startDate > ?1
Before | findByStartDateBefore | … where x.startDate < ?1
IsNull | findByAgeIsNull | … where x.age is null
IsNotNull,NotNull | findByAge(Is)NotNull | … where x.age not null
Like | findByFirstnameLike | … where x.firstname like ?1
NotLike | findByFirstnameNotLike | … where x.firstname not like ?1
StartingWith | findByFirstnameStartingWith | … where x.firstname like ?1(parameter bound with appended %)
EndingWith | findByFirstnameEndingWith | … where x.firstname like ?1(parameter bound with prepended %)
Containing | findByFirstnameContaining | … where x.firstname like ?1(parameter bound wrapped in %)
OrderBy | findByAgeOrderByLastnameDesc | … where x.age = ?1 order by x.lastname desc
Not | findByLastnameNot | … where x.lastname <> ?1
In | findByAgeIn(Collection<Age> ages) | … where x.age in ?1
NotIn | findByAgeNotIn(Collection<Age> ages) | … where x.age not in ?1
True | findByActiveTrue() | … where x.active = true
False | findByActiveFalse() | … where x.active = false
IgnoreCase | findByFirstnameIgnoreCase | … where UPPER(x.firstame) = UPPER(?1)


待更新....



**参考**

* [Spring Data JPA官网文档](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)