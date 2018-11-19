## Hotnode 公共 API 服务 v1.0

Hotnode是区块链行业全球化数据服务和协作平台，致力于成为区块链的Crunchbase+Bloomberg。通过数据挖掘和处理组建行业数据库，在此基础上进行模型建立和数据分析，设计AI数据产品，并对外进行API输出，打造行业基础设施；通过提供工具，服务行业各类角色，吸引入驻，形成一定粘性，成为区块链行业的全球化平台级产品。融入节点资本、金色财经、Hiwa、降维科技生态，扮演生态核心角色。

10月上线以来，已汇聚14000+项目数据、500+投资和服务机构、150+行业研报，打造完整的数据、工具、平台功能支撑，目前已成为区块链行业最大、最全的项目库；同时推出AI数据产品，向行业开放API，邀请各方角色入驻。

以下为 API 的详细接口文档，如有疑问，请提交到 issues 中，我们会尽快回复。

#### API 域名

http://api.open.hotnode.cn

#### 0. 分页参数

##### 请求参数 (HTTP GET)
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
per-page | int| 每页容量 | 20 | 上限300
page | int| 请求页码 | 1 | -

##### 响应参数 (HTTP HEADER)
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
x-pagination-current-page | int| 当前页码 | 1 | -
x-pagination-page-count | int| 分页总页数 | 50 | -
x-pagination-per-page | int| 每页容量 | 20 | -
x-pagination-total-count | int| 条目总数 | 1000 | -



#### 00. 错误提示
```
HTTP/1.1 404 Not Found
Server: nginx
Date: Wed, 14 Nov 2018 02:18:00 GMT
Content-Type: application/json; charset=UTF-8

{
    "name": "Not Found",
    "message": "项目不存在或已下架",
    "code": 0,
    "status": 404
}
```

#### 1. 项目列表

##### 地址
/v1/coins

##### 方法
HTTP/1.1 GET

##### 请求参数
暂无

##### 响应参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
id | int| 编号 | 1 | -
name | string | 名称 | Bitcoin | -
symbol | string | 简称 | BTC | -
icon | url | 图标 | - | -
homepage | url | 官网 | - | -
description | string | 简介 | 这里是简介信息 | -
updated_at | timestamp | 信息更新时间 | 1542098140 | -
finance\_start\_at | timestamp | 幕资开始时间 | 1542098140 | -
finance\_end\_at | timestamp | 幕资结束时间 | 1542098140 | -
finance_status | string | 幕资状态 | 即将开始 | 未设定,即将开始,进行中,已结束
tags | array | 标签列表 | - | -

##### 响应示例
```
[
    {
        "id": 1,
        "name": "Bitcoin",
        "symbol": "btc",
        "icon": "https://assets.coingecko.com/coins/images/1/small/bitcoin.png?1510040391",
        "homepage": "http://www.bitcoin.org",
        "description": "这里是简介信息",
        "updated_at": 1542098140,
        "finance_start_at": 1542098140,
        "finance_end_at": 1542098140,
        "finance_status": "即将开始",
        "tags": [
            {
                "id": 21,
                "name": "社交通讯"
            }
        ]
    }
]
```

#### 2. 项目详情

##### 地址
/v1/coins/{id}

##### 方法
HTTP/1.1 GET

##### 请求参数
暂无

##### 响应参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
id | int| 编号 | 1 | -
name | string | 名称 | Bitcoin | -
symbol | string | Symbol | BTC | -
icon | url | 图标 | - | -
homepage | url | 官网 | - | -
description | string | 简介 | 这里是简介信息 | -
updated_at | timestamp | 信息更新时间 | 1542098140 | -
finance\_start\_at | timestamp | 幕资开始时间 | 1542098140 | -
finance\_end\_at | timestamp | 幕资结束时间 | 1542098140 | -
finance_status | string | 幕资状态 | 即将开始 | -
tags | array | 标签列表 | - | -
regions | array | 国别 | - | -
members | array | 成员 | - | -
white_papers | array | 白皮书 | - | -
investment_orgs | array | 投资机构 | - | -
~~rating_orgs~~ | array | ~~评级机构~~ | - | <font color=#FF0000>正在维护</font>

##### 响应示例
```
{
    "id": 1,
    "name": "Bitcoin",
    "symbol": "btc",
    "icon": "https://assets.coingecko.com/coins/images/1/small/bitcoin.png?1510040391",
    "homepage": "http://www.bitcoin.org",
    "description": "这里是简介信息",
    "updated_at": 1542098140,
    "finance_start_at": 1542098140,
    "finance_end_at": 1542098140,
    "finance_status": "即将开始",
    "tags": [
        {
            "id": 21,
            "name": "社交通讯"
        }
    ],
    "regions": [
        {
            "id": 1,
            "name": "中国"
        },
        {
            "id": 2,
            "name": "美国"
        }
    ],
    "members": [
        {
            "id": 170504,
            "name": "Juan Carlos Ruiz",
            "title": "CEO",
            "profile_pic": "http://hotnode-production-file.oss-cn-beijing.aliyuncs.com/profile_pic/20181106/9HSVL7ZHfrbHriYVcpfaRshKB1tLepBJn4j5uqYLljUT2l.jpeg",
            "introduction": "这里是成员简介",
        }
    ]
    "white_papers": [
        {
            "id": 6337,
            "filename": "白皮书",
            "path_url": "http://hotnode-production-file.oss-cn-beijing.aliyuncs.com/white_papers/20180918/AIHQU0zCTcjGbiPiyANLBbXLdXi5AgI7zFyDqguXON2LNx.pdf",
            "created_at": 1537216321,
            "comment": "这里是一些说明信息"
        }
    ],
    "investment_orgs": [
        {
            "id": 155,
            "name": "投资机构"
        }
    ],
    "rating_orgs": [
        {
            "id": 8378,
            "rating_name": "评级机构",
            "grade": "A+"
        }
    ]
}
```
#### 3. 上所公告

##### 地址
/v1/news

##### 方法
HTTP/1.1 GET

##### 请求参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
coin_id | int| 项目编号 | 1 | 可选参数

##### 响应参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
id | int| 编号 | 1 | -
coin_id | int | 项目编号 | 2069 | -
coin_name | string | 项目 | Bitcoin | -
title | string | 主标题 | - | -
logo | url | 图标 | - | -
subtitle | string | 副标题 | - | -
content | string | 简要内容, 不超过64个字符 | - | text/plain
original_link | url | 原始链接 | - | -
type | string | 内容类型 | 上所公告 | 上所公告,快讯,交易所公告,站内公告
created_at | timestamp | 生成时间 | 1540108220 | -

##### 响应示例
```
[
    {
        "id": 39759,
        "coin_id": 2069,
        "coin_name": "Bitcoin",
        "title": "主标题",
        "logo": "http://domain.com/pic.png",
        "subtitle": "副标题",
        "content": "纯文本简略内容(64字符以内)",
        "original_link": "https://mxc-exchange.zendesk.com/hc/zh-cn/articles/360018512511",
        "type": "上所公告",
        "created_at": 1540108220
    }
]
```

#### 4. 上所公告详情

##### 地址
/v1/news/{id}

##### 方法
HTTP/1.1 GET

##### 请求参数
暂无

##### 响应参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
id | int | 编号 | 1 | -
coin_id | int | 项目编号 | 2069 | -
coin_name | string | 项目 | Bitcoin | -
title | string | 主标题 | - | -
logo | url | 图标 | - | -
subtitle | string | 副标题 | - | -
content | string | 富文本详细内容 | - | text/html
original_link | url | 原始链接 | - | -
type | string | 内容类型 | 上所公告 | 上所公告,快讯,交易所公告,站内公告
created_at | timestamp | 生成时间 | 1540108220 | -

##### 响应示例
```
[
    {
        "id": 39759,
        "coin_id": 2069,
        "coin_name": "Bitcoin",
        "title": "主标题",
        "logo": "http://domain.com/pic.png",
        "subtitle": "副标题",
        "content": "富文本详内容",
        "original_link": "https://mxc-exchange.zendesk.com/hc/zh-cn/articles/360018512511",
        "type": "上所公告",
        "created_at": 1540108220
    }
]
```
