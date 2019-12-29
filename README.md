# htmls

## 开放API查询

    http://api.asilu.com/#geo

## json转jsonp
    
    https://jsonp.afeld.me/

## 有道云翻译jsonp API
 详细使用参考[有道云翻译API](http://fanyi.youdao.com/openapi?path=web-mode)
 
### API使用说明
数据接口

    http://fanyi.youdao.com/openapi.do?keyfrom=<keyfrom>&key=<key>&type=data&doctype=<doctype>&version=1.1&q=要翻译的文本
版本：1.1，请求方式：get，编码方式：utf-8  
主要功能：中英互译，同时获得有道翻译结果和有道词典结果（可能没有）  
参数说明：  
　type - 返回结果的类型，固定为data   
　doctype - 返回结果的数据格式，xml或json或jsonp  
　version - 版本，当前最新版本为1.1     
　q - 要翻译的文本，必须是UTF-8编码，字符长度不能超过200个字符，需要进行urlencode编码   
　only - 可选参数，dict表示只获取词典数据，translate表示只获取翻译数据，默认为都获取    
　注： 词典结果只支持中英互译，翻译结果支持英日韩法俄西到中文的翻译以及中文到英语的翻译    
errorCode：
　0 - 正常
　20 - 要翻译的文本过长
　30 - 无法进行有效的翻译
　40 - 不支持的语言类型
　50 - 无效的key
　60 - 无词典结果，仅在获取词典结果生效

#### json数据格式举例
    http://fanyi.youdao.com/openapi.do?keyfrom=<keyfrom>&key=<key>&type=data&doctype=json&version=1.1&q=good

    {
        "errorCode":0
        "query":"good",
        "translation":["好"], // 有道翻译
        "basic":{ // 有道词典-基本词典
            "phonetic":"gʊd"
            "uk-phonetic":"gʊd" //英式发音
            "us-phonetic":"ɡʊd" //美式发音
            "explains":[
                "好处",
                "好的"
                "好"
            ]
        },
        "web":[ // 有道词典-网络释义
            {
                "key":"good",
                "value":["良好","善","美好"]
            },
            {...}
        ]
    }

#### jsonp数据格式举例
    http://fanyi.youdao.com/openapi.do?keyfrom=<keyfrom>&key=<key>&type=data&doctype=jsonp&callback=show&version=1.1&q=API

    show({
        "errorCode":0
        "query":"API",
        "translation":["API"], // 有道翻译
        "basic":{ // 有道词典-基本词典
            "explains":[
                "abbr. 应用程序界面（Application Program Interface）；..."
            ]
        },
        "web":[ // 有道词典-网络释义
            {
                "key":"API",
                "value":["应用程序接口(Application Programming Interface)","应用编程接口","应用程序编程接口","美国石油协会"]
            },
            {...}
        ]
    });
    
### 划词翻译

    <div id="YOUDAO_SELECTOR_WRAPPER" style="display:none; margin:0; border:0; padding:0; width:320px; height:240px;"></div>
    <script type="text/javascript" src="http://fanyi.youdao.com/openapi.do?keyfrom=<keyfrom>&key=<key>&type=selector&version=1.2&translate=on" charset="utf-8"></script>

### 有道词典

    <div id="YOUDAO_DICTER_WRAPPER" style="margin:0; border:0; padding:0; width:320px; height:240px;"></div>
    <script type="text/javascript" src="http://fanyi.youdao.com/openapi.do?keyfrom=<keyfrom>&key=<key>&type=dicter&version=1.2&select=on&translate=on" charset="utf-8"></script>

### 有道翻译

    <div id="YOUDAO_FANYIER_WRAPPER" style="margin:0; border:0; padding:0; width:320px; height:240px;"></div>
    <script type="text/javascript" src="http://fanyi.youdao.com/openapi.do?keyfrom=<keyfrom>&key=<key>&type=fanyier&version=1.2&select=on" charset="utf-8"></script>

### 说明
有道词典开放平台对上述API有如下说明。 但是经测试，目前依旧可以使用。  

- 使用API key 时，请求频率限制为每小时1000次，超过限制会被封禁。
- 有道翻译 API 平台已经全面升级，当前平台的key申请已经停止，请前往新平台有道智云申请及后续使用。
- 此平台将于 2018-12-31 后停止运行，敬请尽快升级。

### keyfrom与key
可用key  

keyfrom|key  
-|-  
Go-English|1346410123  
github-wdict|619541059  
ice-blog-home|1274584216   
httponnection|316264537  
ArticleBreaker|1968023498
qiyunkj|330102425
zhengwen&key|1318083984
findtrth|678238549



