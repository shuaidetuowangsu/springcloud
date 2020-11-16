### 阿里巴巴java开发手册约定工程结构
java企业级开发一般使用springboot框架来进行应用功能的开发，创建出来的项目一般可分为
1. annotation(注解包)
2. aspect(切面包)
3. config(配置包)
4. constant(常量包)
5. controller(控制层包)
6. service(业务包)
7. filter(业务包)
8. mapper(数据包)
9. utils(工具类包)
10. domain(实体包)
11. dto(服务层传输对象包)
12. bo(业务对象)
13. vo(传输层包)
- 上述也可根据包名换成model进行分模块开发
- ![avatar](d:\\\Users\\\caoming\\\Desktop\\\tms-merchant工作流程图.jpg "test")
#### 多表查询返回对象处理
* 新建数据传输类（DTO）,例如MemberDTO包含很多DO对应的信息
* 写一个方法把DO转化成DTO,一个DTO包含的数据可能来自好几个DO,就像你现在需要传输Member的数据，如果需要其他表的一些属性怎么办。
* DO是保持和数据库一致的，DTO是保持跟外界交互一致的，这样在数据或者业务发生变动的时候，可以灵活的调整。
千万不要把DO直接拿来做数据传输,这样不利于扩展
### 一些注意事项
1. Contorller层参数传递建议不要使用HashMap，建议使用数据模型定义

2. Controller层里可以做参数校验、异常抛出等操作，但建议不要放太多业务逻辑，业务逻辑尽量放到Service层代码中去做

3. Service层做实际业务逻辑，可以按照功能模块做好定义和区分，相互可以调用

4. 功能模块Service之间引用时，建议不要渗透到DAO层（或者mapper层），基于Service层进行调用和复用比较合理

5. 业务逻辑层Service和数据库DAO层的操作对象不要混用。Controller层的数据对象不要直接渗透到DAO层（或者mapper层）；同理数据表实体对象Entity也不要直接传到Controller层进行输出或展示
