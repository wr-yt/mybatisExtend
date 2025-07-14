### 1. 将  rdp-modules/rdp-fwjc/lib/com.zip 这个zip 解压 放到 maven 仓库的对应文件夹下面

2. 使用方法:

   1. ​	字段规则 filter_比较类型数据类型__条件字段

      > `filter_LIKES_nickName`=12 :   `LIKE: 模糊查询 ` `S: 字符串类型` `nickName: 条件字段`
      >
      > ##### 比较类型: 
      >
      > > ```java
      > > public enum MatchType {
      > >     /**
      > >      * 等于
      > >      */
      > >     EQ,
      > >     /**
      > >      * 不等于
      > >      */
      > >     NE,
      > >     /**
      > >      * 模糊查询
      > >      */
      > >     LIKE,
      > >     /**
      > >      * 左模糊查询
      > >      */
      > >     LLIKE,
      > >     /**
      > >      * 右模糊模糊查询
      > >      */
      > >     RLIKE,
      > >     /**
      > >      * 小于
      > >      */
      > >     LT,
      > >     /**
      > >      * 大于
      > >      */
      > >     GT,
      > >     /**
      > >      * 小于等于
      > >      */
      > >     LE,
      > >     /**
      > >      * 大于等于
      > >      */
      > >     GE;
      > > }
      > > ```
      >
      > > ##### 数据类型:
      > >
      > > > ```java
      > > > public enum PropertyType {
      > > > 
      > > >     /**
      > > >      * 字符串
      > > >      */
      > > >     S(String.class),
      > > >     /**
      > > >      * int 类型
      > > >      */
      > > >     I(Integer.class),
      > > >     /**
      > > >      * long 类型
      > > >      */
      > > >     L(Long.class),
      > > >     /**
      > > >      * 双浮点
      > > >      */
      > > >     N(Double.class),
      > > >     /**
      > > >      * 日期
      > > >      */
      > > >     D(Date.class),
      > > >     /**
      > > >      * bool
      > > >      */
      > > >     B(Boolean.class),
      > > >     /**
      > > >      *
      > > >      */
      > > >     DL(Long.class);
      > > > 
      > > >     private Class<?> clazz;
      > > > 
      > > >     PropertyType(Class<?> clazz) {
      > > >         this.clazz = clazz;
      > > >     }
      > > > 
      > > >     public Class<?> getValue() {
      > > >         return this.clazz;
      > > >     }
      > > > }
      > > > ```
      > >
      > > ##### 条件字段:
      > >
      > > > 与表对应的实体 字段名保持一致
      >
      > #### 特别的: OR
      >
      > > `filter_LIKES_nickName_OR_LIKES_remark=12`
      > >
      > > > 表示 查询 
      > > >
      > > > ```sql
      > > > (nickName lile '%12%' or remark like '%12%')
      > > > ```
      > > >
      > > > 
