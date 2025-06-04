# DataFlex

**DataFlex** 是一个灵活高效的数据获取与查询工具，支持通过配置方式动态添加多种数据源，并为每种数据源提供定制化的查询模板，以满足多样化的数据查询需求。

## 目录
1. [项目简介](#项目简介)
2. [主要功能](#主要功能)
3. [安装与配置](#安装与配置)
4. [使用方法](#使用方法)
5. [支持的数据源](#支持的数据源)
6. [配置示例](#配置示例)
7. [开发与贡献](#开发与贡献)
8. [常见问题](#常见问题)
9. [许可证](#许可证)

## 项目简介
在现代数据驱动的应用场景中，数据来源日益多样化，从传统的数据库到新兴的云服务，数据获取和查询的需求也变得复杂多变。**DataFlex** 应运而生，旨在提供一个通用且灵活的解决方案，通过简单的配置即可接入多种数据源，并通过预定义的查询模板高效地获取数据。

## 主要功能
- **多数据源支持**：支持多种类型的数据源，包括但不限于关系型数据库（如 MySQL、PostgreSQL）、NoSQL 数据库（如 MongoDB）、API 接口、文件系统等。
- **动态配置**：通过配置文件或界面，用户可以轻松添加和管理数据源及其查询模板。
- **灵活的查询模板**：为每种数据源定义查询模板，支持参数化查询，满足复杂的数据查询需求。
- **高效的数据处理**：优化的查询引擎，确保数据获取的高效性和稳定性。
- **易于扩展**：支持插件式扩展，方便开发者根据需求添加新的数据源或查询功能。

## 安装与配置
### 环境要求
- **操作系统**：支持主流操作系统（Windows、Linux、macOS）。
- **Python**：推荐使用 Python 3.8 及以上版本。
- **依赖库**：项目依赖于多个 Python 库，如 `requests`、`pymysql`、`pymongo` 等。

### 安装步骤
1. **克隆项目**
   ```bash
   git clone https://github.com/your-repo/DataFlex.git
   cd DataFlex
   ```

2. **安装依赖**
   ```bash
   pip install -r requirements.txt
   ```

3. **配置文件**
   - 复制 `config.example.yml` 为 `config.yml`，并根据需要修改配置内容。
   - 示例配置文件结构：
     ```yaml
     data_sources:
       - name: mysql_db
         type: mysql
         host: localhost
         port: 3306
         user: your_username
         password: your_password
         database: your_database
         query_template: "SELECT * FROM your_table WHERE column = '{param}'"
     ```

4. **启动项目**
   ```bash
   python main.py
   ```

## 使用方法
### 查询数据
- 通过命令行工具或提供的 API 接口，根据配置的查询模板和参数执行数据查询。
- 示例：
  ```bash
  python query.py --source mysql_db --param your_value
  ```

### 添加新数据源
- 在 `config.yml` 文件中添加新的数据源配置，指定类型、连接参数和查询模板。
- 示例：
  ```yaml
  - name: api_service
    type: api
    url: https://api.example.com/data
    query_template: "https://api.example.com/data?param={param}"
  ```

## 支持的数据源
- **关系型数据库**
  - MySQL
  - PostgreSQL
- **NoSQL 数据库**
  - MongoDB
- **API 接口**
  - RESTful API
  - GraphQL API
- **文件系统**
  - CSV 文件
  - JSON 文件

## 配置示例
以下是一个完整的配置文件示例，展示了如何配置多种数据源：
```yaml
data_sources:
  - name: mysql_db
    type: mysql
    host: localhost
    port: 3306
    user: your_username
    password: your_password
    database: your_database
    query_template: "SELECT * FROM your_table WHERE column = '{param}'"

  - name: mongodb_collection
    type: mongodb
    host: localhost
    port: 27017
    database: your_mongo_db
    collection: your_collection
    query_template: "{'field': '{param}'}"

  - name: api_service
    type: api
    url: https://api.example.com/data
    query_template: "https://api.example.com/data?param={param}"
```

## 开发与贡献
欢迎开发者参与 **DataFlex** 的开发和改进！以下是参与贡献的步骤：
1. **Fork 项目**：在 GitHub 上 Fork 本项目。
2. **创建分支**：在本地创建一个新的分支进行开发。
3. **提交代码**：完成开发后，提交代码并通过 Pull Request 提交至主仓库。
4. **遵守规范**：请遵循项目的代码规范和提交规范。

## 常见问题
### Q: 如何添加新的数据源类型？
A: 可以通过扩展项目的数据源适配器模块，实现新的数据源连接逻辑，并在配置文件中注册。

### Q: 查询模板支持哪些参数化方式？
A: 查询模板支持通过 `{param}` 占位符进行参数化替换，用户可以在查询时动态传入参数值。

## 许可证
**DataFlex** 项目遵循 [Apache License 2.0](LICENSE)。欢迎使用和分享！

---
