## Hotnode 公共 API 服务 v1.1

Hotnode是区块链行业全球化数据服务和协作平台，致力于成为区块链的Crunchbase+Bloomberg。通过数据挖掘和处理组建行业数据库，在此基础上进行模型建立和数据分析，设计AI数据产品，并对外进行API输出，打造行业基础设施；通过提供工具，服务行业各类角色，吸引入驻，形成一定粘性，成为区块链行业的全球化平台级产品。融入节点资本、金色财经、Hiwa、降维科技生态，扮演生态核心角色。

10月上线以来，已汇聚14000+项目数据、500+投资和服务机构、150+行业研报，打造完整的数据、工具、平台功能支撑，目前已成为区块链行业最大、最全的项目库；同时推出AI数据产品，向行业开放API，邀请各方角色入驻。

以下为 API 的详细接口文档，如有疑问，请提交到 issues 中，我们会尽快回复。

#### API 地址

https://api.open.hotnode.cn

#### 目录
1. <a href="#分页参数">分页参数</a>
2. <a href="#错误提示">错误提示</a>
3. <a href="#项目列表">项目列表</a>
4. <a href="#项目详情">项目详情</a>
5. <a href="#上所公告列表">上所公告列表</a>
6. <a href="#上所公告详情">上所公告详情</a>
7. <a href="#DAPP列表">DAPP列表</a>
8. <a href="#DAPP详情">DAPP详情</a>
9. <a href="#DAPP主题列表">DAPP主题列表</a>

#### 1. <a name="分页参数">分页参数</a>

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



#### 2. <a name="错误提示">错误提示</a>
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

#### 3. <a name="项目列表">项目列表</a>

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

#### 4. <a name="项目详情">项目详情</a>

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
#### 5. <a name="上所公告">上所公告</a>

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

#### 6. <a name="上所公告详情">上所公告详情</a>

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

#### 7. <a name="DAPP列表">DAPP列表</a>

##### 地址
/v1/dapps

##### 方法
HTTP/1.1 GET

##### 请求参数
暂无

##### 响应参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
id | int| 编号 | 1 | -
topic_id | int | 主题编号 | 254 | -
title | string | 游戏名称 | EOS骑士 | -
description | string | 简介 | - | -
logo | url | 图标 | - | -
language | string | 语言 | - | -
source | string | 来源 | - | dapp_review
homepage | url | 官网地址 | 上所公告 | 
type | string | 类型 | dapp, dapp_update | -
updated_at | timestamp | 更新时间 | 1540108220 | -
created_at | timestamp | 生成时间 | 1540108220 | -
tags | array | 标签 |  | -

##### 响应示例
```
[
    {
        "id": 648,
        "topic_id": 5,
        "title": "EOS骑士",
        "description": "这里是简介",
        "logo": "",
        "language": "zh_CN",
        "source": "dapp_review",
        "is_save": 2,
        "homepage": "http://eosknights.io/",
        "type": "dapp",
        "updated_at": 1544092958,
        "created_at": 1544092958,
        "tags": [
            {
                "id": 17,
                "name": "角色扮演"
            }
        ],
        "topic": {
            "id": 5,
            "name": "eos"
        }
    }
]
```

#### 8. <a name="DAPP详情">DAPP详情</a>

##### 地址
/v1/dapps/{id}

##### 方法
HTTP/1.1 GET

##### 请求参数
暂无

##### 响应参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
id | int| 编号 | 1 | -
topic_id | int | 主题编号 | 254 | -
title | string | 游戏名称 | EOS骑士 | -
description | string | 简介 | - | -
logo | url | 图标 | - | -
language | string | 语言 | - | -
source | string | 来源 | - | dapp_review
homepage | url | 官网地址 | 上所公告 | 
type | string | 类型 | dapp, dapp_update | -
date | timestamp | 时间 | 2018-12-09 | -
tags | array | 标签 |  | -
topic | array | 主题 |  | -
social_networks | array | 社交媒体 |  | -
base_stats | object | 基础统计 |  | -
week\_base\_stats | array | 每周统计 |  | -
balance | string | 余额 |  | -
dau\_last\_day | string | 24活跃用户 |  | -
volume\_last\_day | string | 24h交易额 |  | -
tx\_last\_day | string | 24h交易笔数 |  | -

##### 响应示例
```
{
    "id": 648,
    "topic_id": 5,
    "title": "EOS骑士",
    "description": "这里是简介",
    "logo": "",
    "language": "zh_CN",
    "source": "dapp_review",
    "is_save": 2,
    "homepage": "http://eosknights.io/",
    "type": "dapp",
    "updated_at": 1544092958,
    "created_at": 1544092958,
    "tags": [
        {
            "id": 17,
            "name": "角色扮演"
        }
    ],
    "topic": {
        "id": 5,
        "name": "eos"
    },
    "social_networks": [
        {
            "id": 511,
            "dapp_id": 648,
            "name": "twitter",
            "link_url": "https://twitter.com/funcityone"
        }
    ],
    "base_stats": {
        "id":1,
        "dapp_id":648,
        "balance":"372.50",
        "dau_last_day":"84",
        "volume_last_day":"1,459.82",
        "volume_last_week":"9,815.48",
        "tx_last_day":"6,757",
        "tx_last_week":"49515",
        "date":"2018-12-09",
        "updated_at":1544082041,
        "created_at":1544065696
    },
    "week_base_stats": [
        {
            "id":1,
            "dapp_id":648,
            "balance":"372.50",
            "dau_last_day":"84",
            "volume_last_day":"1,459.82",
            "volume_last_week":"9,815.48",
            "tx_last_day":"6,757",
            "tx_last_week":"49515",
            "date":"2018-12-09",
            "updated_at":1544082041,
            "created_at":1544065696
        },
        {
            "id":2,
            "dapp_id":648,
            "balance":"29.88",
            "dau_last_day":"68",
            "volume_last_day":"16.76",
            "volume_last_week":"114.61",
            "tx_last_day":"137",
            "tx_last_week":"1138",
            "date":"2018-12-08",
            "updated_at":1544082038,
            "created_at":1544082038
        },
        {
            "id":3,
            "dapp_id":648,
            "balance":"0.00",
            "dau_last_day":"66",
            "volume_last_day":"0.00",
            "volume_last_week":"0.00",
            "tx_last_day":"212",
            "tx_last_week":"786",
            "date":"2018-12-07",
            "updated_at":1544082038,
            "created_at":1544082038
        },
        {
            "id":4,
            "dapp_id":648,
            "balance":"0.00",
            "dau_last_day":"73",
            "volume_last_day":"0.00",
            "volume_last_week":"0.00",
            "tx_last_day":"2,866",
            "tx_last_week":"17576",
            "date":"2018-12-06",
            "updated_at":1544082040,
            "created_at":1544082040
        },
        {
            "id":5,
            "dapp_id":648,
            "balance":"708.26",
            "dau_last_day":"84",
            "volume_last_day":"0.61",
            "volume_last_week":"17.11",
            "tx_last_day":"102",
            "tx_last_week":"454",
            "date":"2018-12-05",
            "updated_at":1544082043,
            "created_at":1544082043
        },
        {
            "id":6,
            "dapp_id":648,
            "balance":"21.69",
            "dau_last_day":"104",
            "volume_last_day":"4.78",
            "volume_last_week":"69.88",
            "tx_last_day":"167",
            "tx_last_week":"2102",
            "date":"2018-12-04",
            "updated_at":1544082045,
            "created_at":1544082045
        },
        {
            "id":7,
            "dapp_id":648,
            "balance":"9.05",
            "dau_last_day":"59",
            "volume_last_day":"17.51",
            "volume_last_week":"95.95",
            "tx_last_day":"162",
            "tx_last_week":"940",
            "date":"2018-12-03",
            "updated_at":1544082096,
            "created_at":1544082096
        }
    ]
}
```
#### 9. <a name="DAPP主题列表">DAPP主题列表</a>

##### 地址
/v1/dapps/topics

##### 方法
HTTP/1.1 GET

##### 请求参数
暂无

##### 响应参数
字段 | 类型 | 释义 | 示例 | 备注
---|---|---|---|---
id | int| 编号 | 1 | -
name | string | 主题名称 | tron | -
order | int | 排序 | 100 | -


##### 响应示例
```
[
    {
        "id": 6,
        "name": "tron",
        "order": 1000
    }
]
```

