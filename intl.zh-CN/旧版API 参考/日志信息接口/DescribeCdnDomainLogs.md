# DescribeCdnDomainLogs {#reference_srr_cyc_5db .reference}

获取指定域名的原始访问日志的下载地址。

**说明：** 日志内容最长保留一个月。

## 请求参数 {#section_rxs_wnz_5db .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeCdnDomainLogs| 系统规定参数。取值：

 DescribeCdnDomainLogs

 |
|DomainName|String|是|www.yourdomain.com| 域名（只支持单个查询）。

 |
|EndTime|String|否|2017-12-22T08:00:00:00Z| -   结束时间需大于起始时间。
-   起止时间和结束时间，间隔不超过一年。
-   获取日期格式按照ISO8601表示法，并使用UTC时间。
-   例如：2016-10-20T04:00:00Z。

 |
|LogDay|String|否|2015-05-24| 要获取日志的天。

-   格式yyyy-MM-dd。
-   LogDay与StartTime、EndTime指定其一即可。
-   默认值：当天

 |
|PageNumber|Long|否|2| 取得第几页。

 取值范围：\>1的任意整数。

 |
|PageSize|Long|否|300| 分页大小。

-   最大值：1000
-   取值范围：1~1000之前的任意整数。
-   默认值：300

 |
|StartTime|String|否|2017-12-21T08:00:00:00Z| 获取日志起始时间点。

-   日期格式按照ISO8601表示法，并使用UTC时间。
-   例如：2016-10-20T04:00:00Z。

 |

## 返回参数 {#section_vkr_f4z_5db .section}

|参数|类型|示例值|描述|
|:-|:-|:--|:-|
|PageNumber|Long|1| 返回数据的页码。

 |
|PageSize|Long|100| 整页大小。

 |
|TotalCount|Long|3| 总条数。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8| 请求ID。

 |
|DomainLogModel| | | 日志模型。

 |
|└DomainName|String|gc.ggter.com| 域名。

 |
|└DomainLogDetails| | | DomainLogDetail组成的数据。

 |
|└LogPath|String|cdnlog.cn-hangzhou.oss.aliyun-inc.com/gc.ggter.com/2015\_05\_23/gc.ggter.com\_2015\_05\_23\_1100\_1200.gz?OSSAccessKeyId\\u003d3xmgf7JheOfOTUTf\\u0026Expires\\u003d1432539994\\u0026Signature\\u003d7Ly4ccKN3afzAGYyWDbxBcOcn2I%3D| 日志路径。

 |
|└StartTime|String|2017-12-21T08:00:00:00Z| 开始时间。

 |
|└EndTime|String|2017-12-22T08:00:00:00Z| 结束时间。

 |
|└LogSize|Long|257| 日志大小。

 |
|└LogName|String|gc.ggter.com\_2015\_05\_23\_1100\_1200.gz| 日志名称。

 |

## 示例 {#section_fb4_44z_5db .section}

**请求示例**

```
https://cdn.aliyuncs.com?Action=DescribeCdnDomainLogs&DomainName=gc.ggter.com&LogDay=2015-05-24&公共请求参数
```

**正常返回示例**

-   JSON格式

    ```
    {
        "DomainLogModel":{
            "DomainLogDetails":{
                "DomainLogDetail":[
                    {
                        "EndTime":"2015-05-23T04:00:00Z",
                        "LogName":"gc.ggter.com_2015_05_23_1100_1200.gz",
                        "LogPath":"cdnlog.cn-hangzhou.oss.aliyun-inc.com/gc.ggter.com/2015_05_23/gc.ggter.com_2015_05_23_1100_1200.gz?OSSAccessKeyId=3xmgf7JheOfOTUTf&Expires=1432539994&Signature=7Ly4ccKN3afzAGYyWDbxBcOcn2I%3D",
                        "LogSize":257,
                        "StartTime":"2015-05-23T03:00:00Z"
                    },
                    {
                        "EndTime":"2015-05-23T08:00:00Z",
                        "LogName":"gc.ggter.com_2015_05_23_1500_1600.gz",
                        "LogPath":"cdnlog.cn-hangzhou.oss.aliyun-inc.com/gc.ggter.com/2015_05_23/gc.ggter.com_2015_05_23_1500_1600.gz?OSSAccessKeyId=3xmgf7JheOfOTUTf&Expires=1432539994&Signature=dMv7VqPqZHXVbKPmorGIvylC66c%3D",
                        "LogSize":194,
                        "StartTime":"2015-05-23T07:00:00Z"
                    },
                    {
                        "EndTime":"2015-05-23T14:00:00Z",
                        "LogName":"gc.ggter.com_2015_05_23_2100_2200.gz",
                        "LogPath":"cdnlog.cn-hangzhou.oss.aliyun-inc.com/gc.ggter.com/2015_05_23/gc.ggter.com_2015_05_23_2100_2200.gz?OSSAccessKeyId=3xmgf7JheOfOTUTf&Expires=1432539994&Signature=FpSQCbgNcxCBYIxKVoKC8mGghUQ%3D",
                        "LogSize":258,
                        "StartTime":"2015-05-23T13:00:00Z"
                    }
                ]
            },
            "DomainName":"gc.ggter.com",
            "PageNumber":1,
            "PageSize":100,
            "TotalCount":3
        },
        "RequestId":"1805F349-0A2B-41D9-B4AD-33632AFC27F1"
    }
    ```


**异常返回示例**

-   JSON格式

    ```
    {
        "Code":"InternalError",
        "HostId":"cdn.aliyuncs.com",
        "Message":"The request processing has failed due to some unknown error.",
        "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
    }
    ```


