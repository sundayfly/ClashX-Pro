# 自用整合 ClashX Pro 分流

### ClashX Pro 下载地址

[ClashX Pro Download](https://install.appcenter.ms/users/clashx/apps/clashx-pro/distribution_groups/public)

### 懒人配置参考！

[config.yaml](https://raw.githubusercontent.com/Semporia/ClashX-Pro/master/config.yaml)

### 远程引用分流规则

```yaml

# 代理节点
proxy-providers:
  # 所有节点
  机场名:
    type: http
    path: ./Server/机场名.yaml
    url: 订阅连接
    interval: 3600
    filter: '节点关键词'
    health-check:
        enable: true
        url: http://www.gstatic.com/generate_204
        interval: 3600

# 代理组策略
proxy-groups:

# 策略组说明

# 「Proxy」是代理规则策略，它可以指定为某个节点或嵌套一个其他策略组，如：「url-test」（自动测试）、「Fallback」或「load-balance」（负载均衡）的策略组

  - { name: "MATCH", type: select, proxies: ["Proxy"]} 
  - { name: "Apple", type: select, proxies: ["DIRECT"], use: ["United States","Japan"]}
  - { name: "Adobe", type: url-test, use: ["United States"]}
  - { name: "Amazon", type: url-test, use: ["United States"]}
  - { name: "China", type: select, proxies: ["DIRECT"]}
  - { name: "Dler", type: select, use: ["Hong Kong","United States","Dler Cloud"]}
  - { name: "Facebook", type: url-test, use: ["Hong Kong"]}
  - { name: "GitHub", type: url-test, use: ["Hong Kong"]}
  - { name: "Google", type: url-test, use: ["United States"]}
  - { name: "Microsoft", type: select, proxies: ["DIRECT"], use: ["United States"]}
  - { name: "Netflix", type: url-test, use: ["United States"]}
  - { name: "Speedtest", type: select, proxies: ["DIRECT"]} 
  - { name: "Steam", type: url-test, use: ["United States"]}
  - { name: "Spotify", type: url-test, use: ["United States"]}
  - { name: "Telegram", type: url-test, use: ["Hong Kong"]}
  - { name: "Twitter", type: url-test, use: ["Hong Kong"]}
  - { name: "Tencent", type: select, proxies: ["DIRECT"]} 
  - { name: "TencentVideo", type: select, proxies: ["DIRECT"]} 
  - { name: "YouTube", type: url-test, use: ["United States"]}
  - { name: "paypal", type: url-test, use: ["United States"]}
  - { name: "Discord", type: url-test, use: ["United States"]}
  - { name: "Proxy", type: url-test, use: ["Hong Kong","United States"]} 

# 分流规则  
rules:
  - RULE-SET,AdBlock,REJECT
  - RULE-SET,Proxy,Proxy
  - RULE-SET,Apple,Proxy
  - RULE-SET,Adobe,Proxy
  - RULE-SET,Amazon,Proxy
  - RULE-SET,Dler,Proxy
  - RULE-SET,Facebook,Proxy
  - RULE-SET,GitHub,Proxy
  - RULE-SET,Google,Proxy
  - RULE-SET,Microsoft,Proxy
  - RULE-SET,Netflix,Proxy
  - RULE-SET,Speedtest,Proxy
  - RULE-SET,Steam,Proxy
  - RULE-SET,Spotify,Proxy
  - RULE-SET,Telegram,Proxy
  - RULE-SET,Twitter,Proxy 
  - RULE-SET,Tencent,Proxy
  - RULE-SET,TencentVideo,Proxy
  - RULE-SET,YouTube,Youtube
  - RULE-SET,PayPal,Proxy
  - RULE-SET,Discord,Proxy
  - DOMAIN-SUFFIX,live.cn,Proxy
  - DOMAIN-SUFFIX,sub.dler.io,Proxy
  - DOMAIN-SUFFIX,api.suo.yt,Proxy
  - DOMAIN-SUFFIX,dlercloud.com,Proxy
  - DOMAIN-KEYWORD,dlercloud,Proxy

  - DOMAIN-SUFFIX,wps.com,DIRECT
  - DOMAIN-SUFFIX,local,DIRECT
  - IP-CIDR,192.168.0.0/16,DIRECT
  - IP-CIDR,10.0.0.0/8,DIRECT
  - IP-CIDR,172.16.0.0/12,DIRECT
  - IP-CIDR,127.0.0.0/8,DIRECT
  - IP-CIDR,100.64.0.0/10,DIRECT
  - IP-CIDR,172.13.1.32/32,DIRECT

  - GEOIP,CN,DIRECT
  - MATCH,Proxy

rule-providers:
  AdBlock: {type: http, behavior: classical, path: ./Filter/AdBlock, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/AdBlock.yaml, interval: 3600}
  Apple: {type: http, behavior: classical, path: ./Filter/Apple, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Apple.yaml, interval: 3600}
  Adobe: {type: http, behavior: classical, path: ./Filter/Adobe, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Adobe.yaml, interval: 3600}
  Amazon: {type: http, behavior: classical, path: ./Filter/Amazon, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Amazon.yaml, interval: 3600}
  China: {type: http, behavior: classical, path: ./Filter/China, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/China.yaml, interval: 3600}
  Dler: {type: http, behavior: classical, path: ./Filter/Dler, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Dler.yaml, interval: 3600}
  Facebook: {type: http, behavior: classical, path: ./Filter/Facebook, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Facebook.yaml, interval: 3600}
  GitHub: {type: http, behavior: classical, path: ./Filter/GitHub, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/GitHub.yaml, interval: 3600}
  Google: {type: http, behavior: classical, path: ./Filter/Google, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Google.yaml, interval: 3600}
  Microsoft: {type: http, behavior: classical, path: ./Filter/Microsoft, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Microsoft.yaml, interval: 3600}
  Netflix: {type: http, behavior: classical, path: ./Filter/Netflix, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Netflix.yaml, interval: 3600}
  Spotify: {type: http, behavior: classical, path: ./Filter/Spotify, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Spotify.yaml, interval: 3600}
  Speedtest: {type: http, behavior: classical, path: ./Filter/Speedtest, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Speedtest.yaml, interval: 3600}
  Steam: {type: http, behavior: classical, path: ./Filter/Steam, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Steam.yaml, interval: 3600}
  Telegram: {type: http, behavior: classical, path: ./Filter/Telegram, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Telegram.yaml, interval: 3600}
  Twitter: {type: http, behavior: classical, path: ./Filter/Twitter, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Twitter.yaml, interval: 3600}
  Tencent: {type: http, behavior: classical, path: ./Filter/Tencent, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Tencent.yaml, interval: 3600}
  TencentVideo: {type: http, behavior: classical, path: ./Filter/TencentVideo, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/TencentVideo.yaml, interval: 3600}
  YouTube: {type: http, behavior: classical, path: ./Filter/YouTube, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/YouTube.yaml, interval: 3600}
  PayPal: {type: http, behavior: classical, path: ./Filter/PayPal, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/PayPal.yaml, interval: 3600}
  Discord: {type: http, behavior: classical, path: ./Filter/Discord, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Discord.yaml, interval: 3600}
  Proxy: {type: http, behavior: classical, path: ./Filter/Proxy, url: https://raw.fastgit.org/Semporia/Clash/master/Rule/Proxy.yaml, interval: 3600}
```
