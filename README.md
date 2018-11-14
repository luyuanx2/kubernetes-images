# Resource 使用说明

`resource` 模块是对文件上传下载的一个简单封装，应用只需引入相应依赖即可，目前仅支持本地上传和sftp上传。

## 1. 快速开始

### 1.1. 前提

必须是Spring Boot项目。

### 1.2. 如何使用？

完成以下步骤，为您的Spring Boot项目启用Resource。 

1. 在项目依赖中添加 `resource` 如下所示:

   ```xml
       <dependencies>
           ...
   
           <dependency>
               <groupId>me.luyuan.hole</groupId>
               <artifactId>resource</artifactId>
               <version>1.0-SNAPSHOT</version>
           </dependency>
   
           ...
       </dependencies>
   ```

 2. 在项目中注入 `ResourceService`:

    默认注入的是`LocalResourceService`本地资源服务，资源上传到本地磁盘目录

    ```java
        @Autowired
        private ResourceService resourceService;
    ```

### 1.3. 配置Resource

 1. `me.luyuan.hole.resource.home`用来配置资源存储的根目录，如下所示:

    ```properties
    ### 带有用户名密码登录sftp服务器的上传根目录
    me.luyuan.hole.resource.home=sftp://username:password@host/upload/
    ### sftp服务器的上传根目录(前提服务端端已经配置公钥免密登录)
    me.luyuan.hole.resource.home=sftp://host/upload/
    ### 本地磁盘上传根目录
    me.luyuan.hole.resource.home=/data/sftp/upload/
    ```

    > **Note:** 如不配置，默认上传到项目的`resource/_resource`文件夹下

 2. `me.luyuan.hole.resource.uri`用来配置资源服务器的地址，用于定位资源，例如: 

    ```properties
    me.luyuan.hole.resource.uri=http://re.xxx.cn/
    ```

3. `me.luyuan.hole.resource.type`资源类型配置，属性值设置为`local`，在项目启动时自动装载`LocalResourceService`。属性值设为`vfs`,`VFSRsourceService`会被自动装载到Spring上下文。

    ```properties
    me.luyuan.hole.resource.type=local or vfs
    ```

    > **Note:**  不使用该配置，默认自动装载 `LocalResourceService`



## 2. 搭建SFTP服务器
aaaa


