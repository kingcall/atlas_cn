# Hadoop的数据治理和元数据框架

**Git Book 请查看地址：https://mantoudev.com/mantouBook/Atlas_cn/index.html**

>笔者近期在和团队的小伙伴进行数据资产管理方向的探索，本书的翻译基于[Apache Atlas v1.1](https://atlas.apache.org/)版本。希望对大家有帮助，阅读过程中遇到问题欢迎留言或与我联系，欢迎交流。

## 1. 概述
Atlas 是一个可伸缩和可扩展的核心基础治理服务集合 ，使企业能够有效地和高效地满足 Hadoop 中的合规性要求，并允许与整个企业数据生态系统的集成。

Apache Atlas为组织提供开放式元数据管理和治理功能，用以构建其数据资产目录，对这些资产进行分类和管理，并为数据科学家，数据分析师和数据治理团队提供围绕这些数据资产的协作功能。

## 2. 特性
### 2.1 元数据类型 & 实例
- 各种Hadoop和非Hadoop元数据的预定义类型
- 能够为要管理的元数据定义新类型
- 类型可以具有原始属性，复杂属性，对象引用;可以继承其他类型
- 类型(type)实例（称为实体entities）捕获元数据对象详细信息及其关系
- 可以更轻松地进行集成用于处理类型和实例的REST API

### 2.2 分类
- 能够动态创建分类 - 如PII，EXPIRES_ON，DATA_QUALITY，SENSITIVE。
- 分类可以包含属性 - 例如EXPIRES_ON分类中的expiry_date属性。
- 实体(entities)可以与多个分类(classifications)相关联，从而实现更轻松的发现和安全实施。
- 通过血缘传播分类 - 自动确保分类在进行各种处理时遵循数据。

### 2.3 血缘
- 直观的UI，用于在数据流转时，通过各种流程时查看数据。
- 用于访问和更新血缘的REST API。

### 2.4 搜索/发现
- 直观的UI，按类型(type)，分类(classification)，属性值(attribute)或自由文本搜索实体。
- 丰富的REST API，可按复杂条件进行搜索。
- SQL搜索实体的查询语言 - 域特定语言（DSL）。

### 2.5 安全和数据屏蔽
- 用于元数据访问的细粒度安全性，实现对实体实例的访问控制以及添加/更新/删除分类等操作。
- 与Apache Ranger集成可根据与Apache Atlas中的实体相关的分类对数据访问进行授权/数据屏蔽。例如：
    - 谁可以访问分类为PII，SENSITIVE的数据。
    - 客户服务用户只能看到分类为NATIONAL_ID的列的最后4位数字。
