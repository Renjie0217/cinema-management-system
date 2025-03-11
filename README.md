# 影院管理系统
**基于 SpringBoot + Vue 的电影院管理系统**  
一个高效、安全、用户友好的影院管理平台，支持电影信息管理、在线购票、座位分配、数据统计等功能。

## 系统概述
该系统提供完整的影院业务流程管理，从电影排片到用户购票，再到数据分析，实现了影院管理的数字化和智能化。系统架构采用前后端分离设计，保证了良好的扩展性和维护性。

## 技术栈
- **后端**：SpringBoot 2.x, MyBatis-Plus, Java 8  
- **前端**：Vue 2.x, Element-UI, Axios  
- **数据库**：MySQL 5.7  
- **工具**：Maven, Node.js, IDEA/VSCode  

## 功能模块
### 用户端
- **首页浏览**：热映电影、即将上映、票房榜单展示  
- **购票流程**：选择场次、实时选座、在线支付  
- **用户中心**：个人信息管理、订单查询、注册/登录  

### 管理员端
- **影院管理**：影院信息维护、营业时间设置  
- **影厅管理**：座位布局配置、场次排期  
- **影片管理**：电影信息增删改查、海报上传  
- **数据统计**：票房分析、用户行为统计  
- **权限控制**：角色分配、资源权限管理  

## 快速启动
### 环境准备
1. 安装 JDK 1.8、MySQL 5.7、Node.js 14+  
2. 导入数据库脚本（参考 `docs/sql` 目录下的 `schema.sql`）  

### 后端启动
```bash
cd cinema-backend
mvn clean install
mvn spring-boot:run
```

### 前端启动
```bash
cd cinema-frontend
npm install
npm run serve
```

## 数据库设计
- **核心表**：  
  - `sys_movie`（电影信息）  
  - `sys_session`（场次信息）  
  - `sys_bill`（订单信息）  
  - `sys_user`（用户信息）  

## 接口示例
### 用户登录
**请求**：
```java
@PostMapping("/sysUser/login")
public ResponseResult login(@RequestBody SysUserVo sysUserVo) {
    return getResult(sysUserService.login(sysUserVo));
}
```

### 场次查询
**请求**：
```java
@GetMapping("/sysSession")
public ResponseResult findByVo(SysSessionVo sysSessionVo) {
    startPage();
    List<SysSession> list = sysSessionService.findByVo(sysSessionVo);
    return getResult(list);
}
```

## 测试用例
| 模块           | 测试场景               | 预期结果                     |
|----------------|------------------------|------------------------------|
| 用户登录       | 正确/错误凭证          | 成功跳转/提示错误            |
| 购票流程       | 选择座位并支付         | 生成订单，更新座位状态       |
| 影厅管理       | 新增影厅               | 影厅信息持久化至数据库       |

## 项目结构
```
cinema-system/
├── cinema-backend/     # SpringBoot 后端
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/cinema/
│   │   │   │   ├── controller/    # 控制器层
│   │   │   │   ├── service/       # 服务层
│   │   │   │   ├── dao/           # 数据访问层
│   │   │   │   ├── entity/        # 实体类
│   │   │   │   ├── vo/            # 视图对象
│   │   │   │   └── config/        # 配置类
│   │   │   └── resources/         # 配置文件
│   │   └── test/                  # 测试代码
│   └── pom.xml
├── cinema-frontend/    # Vue 前端
│   ├── src/
│   │   ├── components/ # 组件
│   │   ├── views/      # 页面
│   │   ├── router/     # 路由
│   │   ├── store/      # 状态管理
│   │   ├── api/        # 接口封装
│   │   └── assets/     # 静态资源
│   └── package.json
├── docs/               # 文档与 SQL 脚本
│   ├── sql/            # 数据库脚本
│   └── api/            # API 文档
└── README.md
```

## 系统亮点
1. **实时座位选择**：采用WebSocket技术实现多用户实时座位状态同步
2. **数据可视化**：利用ECharts提供丰富的票房和用户行为数据分析图表
3. **响应式设计**：支持PC端和移动端的自适应布局
4. **微服务架构**：模块化设计，为未来扩展做好准备

## 安全特性
- JWT token认证机制
- 防SQL注入处理
- XSS防护
- 敏感数据加密存储

## 贡献与许可
- **贡献**：欢迎提交 Issue 或 PR  
- **许可证**：MIT License  

## 常见问题
1. **Q: 如何修改数据库连接配置?**  
   A: 编辑`cinema-backend/src/main/resources/application.yml`文件中的数据库连接信息。

2. **Q: 默认管理员账号是什么?**  
   A: 默认管理员账号在`docs/sql/schema.sql`中的`sys_user`表初始化数据中定义。

3. **Q: 如何自定义座位布局?**  
   A: 在管理员端的影厅管理模块中，可以通过可视化工具进行座位布局的自定义配置。

**提示**：  
1. 需根据实际路径调整数据库脚本和图片引用。  
2. 配置文件（如 `application.yml`）需填写正确的数据库连接信息。  
3. 管理员默认账号可在 `sys_user` 表中初始化。# 影院管理系统
**基于 SpringBoot + Vue 的电影院管理系统**  
一个高效、安全、用户友好的影院管理平台，支持电影信息管理、在线购票、座位分配、数据统计等功能。


