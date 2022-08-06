# MyBatisGeneratorTools
# MybatisGeneratorTools

## 简介

mybatis逆向工具，用户程序自动生成Mapper接口以及Mapper接口所对应的xml文件

## 使用方式

将相对应的文件包导入，[包已经全部准备在lib文件中]，在source中的

**generatorConfig.xml**文件中添加需要的配置进行生成

----------

## 配置文件如下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
  PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
  "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">

<generatorConfiguration>
   <context id="testTables" targetRuntime="MyBatis3">
      <commentGenerator>
         <!-- 是否去除自动生成的注释 true：是 ： false:否 -->
         <property name="suppressAllComments" value="false" />
         <property name="suppressDate" value="false"/>
      </commentGenerator>
      <!--数据库连接的信息：驱动类、连接地址、用户名、密码 -->
      <jdbcConnection driverClass="com.mysql.cj.jdbc.Driver"
         connectionURL="jdbc:mysql://127.0.0.1:3306/myclass?useSSL=false&amp;serverTimezone=Asia/Shanghai&amp;allowPublicKeyRetrieval=true" userId="root"
         password="a1160124552">
         <property name="nullCatalogMeansCurrent" value="true"/>
      </jdbcConnection>
      <!-- 默认false，把JDBC DECIMAL 和 NUMERIC 类型解析为 Integer，为 true时把JDBC DECIMAL 和 
         NUMERIC 类型解析为java.math.BigDecimal -->
      <javaTypeResolver>
         <property name="forceBigDecimals" value="false" />
      </javaTypeResolver>

      <!-- targetProject:生成PO类的位置 -->
      <javaModelGenerator targetPackage="com.hzh.javaeefinwork2.entity"
         targetProject=".\src">
         <!-- enableSubPackages:是否让schema作为包的后缀 -->
         <property name="enableSubPackages" value="false" />
         <!-- 从数据库返回的值被清理前后的空格 -->
         <property name="trimStrings" value="true" />
      </javaModelGenerator>
        <!-- targetProject:mapper映射文件生成的位置 -->
      <sqlMapGenerator targetPackage="com.hzh.crm.workbench.mapper"
         targetProject=".\src">
         <!-- enableSubPackages:是否让schema作为包的后缀 -->
         <property name="enableSubPackages" value="false" />
      </sqlMapGenerator>
      <!-- targetPackage：mapper接口生成的位置 -->
      <javaClientGenerator type="XMLMAPPER"
         targetPackage="com.hzh.crm.workbench.mapper"
         targetProject=".\src">
         <!-- enableSubPackages:是否让schema作为包的后缀 -->
         <property name="enableSubPackages" value="false" />
      </javaClientGenerator>
      <!-- 指定数据库表 -->
      
      
      <table tableName="classinfo" domainObjectName="ClassInfo"
            enableCountByExample="false" enableUpdateByExample="false"
            enableDeleteByExample="false" enableSelectByExample="false"
            selectByExampleQueryId="false"
      ></table>


      <!--需要新的表就添加新的表，不需要用的的时候就取消掉-->
      <!--<table tableName="tbl_user" domainObjectName="User"
            enableCountByExample="false" enableUpdateByExample="false"
            enableDeleteByExample="false" enableSelectByExample="false"
            selectByExampleQueryId="false"
      ></table>-->



   </context>
</generatorConfiguration>
```

当需要生成多张表的时候，只需要添加相对应的表的信息就可以成功

--------

项目演示效果如下
![演示效果图1](https://github.com/nacey5/MyBatisGeneratorTools/blob/master/Snipaste_MybatisGenerator1_.png)
文件内容和代码示例如下:

