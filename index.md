# intro

easypurchase is arm to provide a startkit for developing payment serverside api/callback handler.

it is based on laravel, omnipay etc. those opensource projects make this happen, thx to all.

i use chinese mainly, and focus on alipay and wechatpay, so my docs will be in chinese language.

easypurchase计划打造一套开源的标准化的聚合支付程序，为开发者快速搭建对接支付提供助力。主要围绕国内最常用的支付宝和微信支付，然后逐步覆盖海内外各种常用APP、H5、web、内购、小程序等支付方式。

技术方案如下：
1. 优先选择MIT协议的开源程序，避免在商用中遇到协议问题
2. 选择Laravel LTS版本提供稳定的基础API平台，一方面支付程序的性能不是关键，一方面Laravel的性能优化我很擅长，有需要付费支持做Laravel性能优化的可以联系我
3. 选择omnipay 3作为聚合支付网关的基础，因为已经它支持了很多的支付渠道
4. 选择guzzleHTTP作为http客户端，文档很详细，所以用起来很方便
5. 选择pingpp-php作为客户端SDK，是的，作为支付网关，既可以直接由客户端调用请求，也可以作为支付中心微服务，由业务方接收客户端数据后透传，实现业务与支付彻底解耦，如果有业务多元发展到一定阶段不知道如何做架构拆分的公司可以联系我
6. 货币暂时只支持人民币CNY，金额统一以分为单位存储unsigned int类型，程序层面考虑网络支付额度限制最大支付金额为10万元，但理论上最大可以支持4千万元。

主要挑战：

开源的底层技术类库只用考虑当前支付方式的参数有没有传够，而如何利用开源技术真正实现一套可插拔的企业级生产可用的支付系统是很难的。

1. 文档要足够清晰
2. 接口要通用化但又要简化不必要的传参
3. 安全问题很重要，越灵活的系统以及开源系统最容易被黑客利用公开的漏洞攻克，比黑盒的容易的多
4. 语言问题，虽然我是坚定的phper，但中国现状是有一定规模的互联网公司盲目的信奉java技术体系，语言选型是一大难，这也是我做这套系统的初衷，因为过去缺乏这种成熟系统，导致开发不得不转为java开发的系统的事情经常发生
