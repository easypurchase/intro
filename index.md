# intro

easypurchase is arm to provide a startkit for developing payment serverside api/callback handler.

it is based on laravel, omnipay etc. those opensource projects make this happen, thx to all.

i use chinese mainly, and focus on alipay and wechatpay, so my docs will be in chinese language.

easypurchase计划打造一套开源的标准化的聚合支付程序，为开发者快速搭建对接支付提供助力。主要围绕国内最常用的支付宝和微信支付，然后逐步覆盖海内外各种常用APP、H5、web、内购、小程序等支付方式。

## 技术方案

1. 优先选择MIT协议的开源程序，避免在商用中遇到协议问题
2. 选择Laravel LTS版本提供稳定的基础API平台，一方面支付程序的性能不是关键，一方面Laravel的性能优化我很擅长，有需要付费支持做Laravel性能优化的可以联系我
3. 选择omnipay 3作为聚合支付网关的基础，因为已经它支持了很多的支付渠道
4. 选择guzzleHTTP作为http客户端，文档很详细，所以用起来很方便
5. 选择pingpp-php作为客户端SDK，是的，作为支付网关，既可以直接由客户端调用请求，也可以作为支付中心微服务，由业务方接收客户端数据后透传，实现业务与支付彻底解耦，如果有业务多元发展到一定阶段不知道如何做架构拆分的公司可以联系我
6. 货币暂时只支持人民币CNY，金额统一以分为单位存储unsigned int类型，程序层面考虑网络支付额度限制最大支付金额为10万元，但理论上最大可以支持4千万元。

## 主要挑战

开源的底层技术类库只用考虑当前支付方式的参数有没有传够，而如何利用开源技术真正实现一套可插拔的企业级生产可用的支付系统是很难的。

1. 文档要足够清晰
2. 接口要通用化但又要简化不必要的传参
3. 安全问题很重要，越灵活的系统以及开源系统最容易被黑客利用公开的漏洞攻克，比黑盒的容易的多
4. 语言问题，虽然我是坚定的phper，但中国现状是有一定规模的互联网公司盲目的信奉java技术体系，语言选型是一大难，这也是我做这套系统的初衷，因为过去缺乏这种成熟系统，导致开发不得不转为java开发的系统的事情经常发生

## 支持支付库

### 主要支持

Gateway | 2.x | 3.x | Composer Package | Maintainer
--- | --- | --- | --- | ---
[Alipay](https://github.com/lokielse/omnipay-alipay) | ✓ | ✓ | lokielse/omnipay-alipay | [Loki Else](https://github.com/lokielse)
[Braintree](https://github.com/thephpleague/omnipay-braintree) | ✓ | ✓ | omnipay/braintree | [Omnipay](https://github.com/thephpleague/omnipay)
[UnionPay](https://github.com/lokielse/omnipay-unionpay) | ✓ | ✓ | lokielse/omnipay-unionpay | [Loki Else](https://github.com/lokielse)
[WechatPay](https://github.com/lokielse/omnipay-wechatpay) | ✓ | ✓ | lokielse/omnipay-wechatpay |  [Loki Else](https://github.com/lokielse)

### 计划支持

Gateway | 2.x | 3.x | Composer Package | Maintainer
--- | --- | --- | --- | ---
[99Bill](https://github.com/laraveler/omnipay-99bill) | - | ✓ | x-class/omnipay-99bill | [Laraveler](https://github.com/laraveler)
[Alipay(Global)](https://github.com/lokielse/omnipay-global-alipay) | ✓  | ✓ | lokielse/omnipay-global-alipay | [Loki Else](https://github.com/lokielse)
[PaymentWall](https://github.com/incube8/omnipay-paymentwall) | ✓ | - | incube8/omnipay-paymentwall | [Del](https://github.com/delatbabel)
[QQ Wallet(QPay)](https://github.com/kuangjy2/omnipay-qpay) | - | ✓ | kuangjy/omnipay-qpay | [Kuang Jiaye](https://github.com/kuangjy2)
[Square](https://github.com/Transportersio/omnipay-square) | ✓ | ✓ | transportersio/omnipay-square | [Transporters.io](https://github.com/Transportersio)
[Starkpay](https://github.com/starkpay/omnipay) | ✓ | ✓ | starkpay/omnipay | [Starkpay](https://github.com/starkpay)
[Stripe](https://github.com/thephpleague/omnipay-stripe) | ✓ | ✓ | omnipay/stripe | [Del](https://github.com/delatbabel)
[Ping++](https://github.com/phoenixg/omnipay-pingpp) | ✓ | - | phoenixg/omnipay-pingpp | [Huang Feng](https://github.com/phoenixg)

### omnipay 3.x 库 看情况做适配
Gateway | 2.x | 3.x | Composer Package | Maintainer
--- | --- | --- | --- | ---
[Authorize.Net](https://github.com/thephpleague/omnipay-authorizenet) | ✓ | ✓ | omnipay/authorizenet | [Jason Judge](https://github.com/judgej)
[CashBaBa](https://github.com/tapos007/omnipay-cashbaba) | ✓ | ✓ | omnipay/cashbaba | [Recursion Technologies Ltd](https://github.com/tapos007)
[Dummy](https://github.com/thephpleague/omnipay-dummy) | ✓ | ✓ | omnipay/dummy | [Del](https://github.com/delatbabel)
[eWAY](https://github.com/thephpleague/omnipay-eway) | ✓ | ✓ | omnipay/eway | [Del](https://github.com/delatbabel)
[Mollie](https://github.com/thephpleague/omnipay-mollie) | ✓ | ✓ | omnipay/mollie | [Barry vd. Heuvel](https://github.com/barryvdh)
[PaymentExpress (DPS)](https://github.com/thephpleague/omnipay-paymentexpress) | ✓ | ✓ | omnipay/paymentexpress | [Del](https://github.com/delatbabel)
[PayPal](https://github.com/thephpleague/omnipay-paypal) | ✓ | ✓ | omnipay/paypal | [Del](https://github.com/delatbabel)
[Sage Pay](https://github.com/thephpleague/omnipay-sagepay) | ✓ | ✓ | omnipay/sagepay | [Jason Judge](https://github.com/judgej)
[SecurePay](https://github.com/thephpleague/omnipay-securepay) | ✓ | ✓ | omnipay/securepay | [Omnipay](https://github.com/thephpleague/omnipay)
[Worldpay Business Gateway](https://github.com/thephpleague/omnipay-worldpay) | ✓ | ✓ | omnipay/worldpay | [Omnipay](https://github.com/thephpleague/omnipay)

### 兼容

Gateway | 2.x | 3.x | Composer Package | Maintainer
--- | --- | --- | --- | ---
[2c2p](https://github.com/dilab/omnipay-2c2p) | ✓ | ✓ | dilab/omnipay-2c2p | [Xu Ding](https://github.com/dilab)
[Adyen](https://github.com/academe/omnipay-adyen) | - | ✓ | academe/omnipay-adyen | [Jason Judge](https://github.com/judgej)
[Affirm](https://github.com/eduardlleshi/omnipay-affirm) | ✓ | ✓ | eduardlleshi/omnipay-affirm | [Eduard Lleshi](https://github.com/eduardlleshi)
[Arca](https://github.com/k3rnel/omnipay-arca) | - | ✓ | k3rnel/omnipay-arca | [Poghos Boyajyan](https://github.com/k3rnel)
[Authorize.Net API](https://github.com/academe/omnipay-authorizenetapi) | - | ✓ | academe/omnipay-authorizenetapi | [Jason Judge](https://github.com/judgej)
[Authorize.Net Recurring Billing](https://github.com/cimpleo/omnipay-authorizenetrecurring) | - | ✓ | cimpleo/omnipay-authorizenetrecurring | [CimpleO](https://github.com/cimpleo)
[Bankart](https://github.com/ampeco/omnipay-bankart) | ✓ | ✓ | ampeco/omnipay-bankart | [Ampeco](https://github.com/ampeco)
[BlueOrange bank](https://github.com/DeH4eG/omnipay-blueorange) | - | ✓ | deh4eg/omnipay-blueorange | [Denis Smolakov](https://github.com/DeH4eG)
[BitPay](https://github.com/hiqdev/omnipay-bitpay) | ✓ | ✓ | hiqdev/omnipay-bitpay | [HiQDev](https://github.com/hiqdev)
[CoinPayments](https://github.com/InkedCurtis/omnipay-coinpayments) | ✓ | ✓ | InkedCurtis/omnipay-coinpayments | [InkedCurtis](https://github.com/InkedCurtis)
[Cybersource](https://github.com/dioscouri/omnipay-cybersource) | ✓ | ✓ | dioscouri/omnipay-cybersource | [Dioscouri Design](https://github.com/dioscouri)
[Datatrans](https://github.com/academe/omnipay-datatrans) | ✓ | ✓ | academe/omnipay-datatrans | [Jason Judge](https://github.com/judgej)
[Docdata Payments](https://github.com/Uskur/omnipay-docdata-payments) | ✓ | ✓ | uskur/omnipay-docdata-payments | [Uskur](https://github.com/Uskur)
[Ebanx](https://github.com/descubraomundo/omnipay-ebanx) | - | ✓ | descubraomundo/omnipay-ebanx | [Descubra o Mundo](https://github.com/descubraomundo/)
[eGHL](https://bitbucket.org/eghl/eghl-omnipay/src/master/) | - | ✓ | e-ghl/omnipay | [Jawad Humayun](https://bitbucket.org/jawad242/)
[eGHL](https://github.com/dilab/omnipay-eghl) | ✓ | ✓ | dilab/omnipay-eghl | [Xu Ding](https://github.com/dilab)
[eCoin](https://github.com/hiqdev/omnipay-ecoin) | ✓ | ✓ | hiqdev/omnipay-ecoin | [HiQDev](https://github.com/hiqdev)
[eSewa](https://github.com/sudiptpa/esewa) | - | ✓ | sudiptpa/omnipay-esewa | [Sujip Thapa](https://github.com/sudiptpa)
[Elavon](https://github.com/lxrco/omnipay-elavon) | ✓ | ✓ | lxrco/omnipay-elavon | [Korri](https://github.com/Korri)
[ePayments](https://github.com/hiqdev/omnipay-epayments) | ✓ | ✓ | hiqdev/omnipay-epayments | [HiQDev](https://github.com/hiqdev)
[ePayService](https://github.com/hiqdev/omnipay-epayservice) | ✓ | ✓ | hiqdev/omnipay-epayservice | [HiQDev](https://github.com/hiqdev)
[Faspay](https://github.com/David-Kurniawan/omnipay-faspay) | ✓ | ✓ | David-Kurniawan/omnipay-faspay | [David](https://github.com/David-Kurniawan)
[FreeKassa](https://github.com/hiqdev/omnipay-freekassa) | ✓ | ✓ | hiqdev/omnipay-freekassa | [HiQDev](https://github.com/hiqdev)
[Fibank](https://github.com/ampeco/omnipay-fibank) | - | ✓ | ampeco/omnipay-fibank | [Ampeco](https://github.com/ampeco)
[GVP (Garanti)](https://github.com/emr/omnipay-gvp) | - | ✓ | emr/omnipay-gvp | [Emre Akinci](https://github.com/emr)
[Icepay Payments](https://github.com/superbrave/omnipay-icepay-payments) | - | ✓ | superbrave/omnipay-icepay-payments | [SuperBrave](https://github.com/superbrave)
[iDram](https://github.com/ptuchik/omnipay-idram) | - | ✓ | ptuchik/omnipay-idram | [Avik Aghajanyan](https://github.com/ptuchik)
[iDeal](https://github.com/deniztezcan/omnipay-ideal) | - | ✓ | deniztezcan/omnipay-ideal | [Deniz Tezcan](https://github.com/deniztezcan)
[Ingenico ePayments](https://github.com/deniztezcan/omnipay-ingenico-epayments) | - | ✓ | deniztezcan/omnipay-ingenico-epayments | [Deniz Tezcan](https://github.com/deniztezcan)
[iPay88](https://github.com/dilab/omnipay-ipay88) | ✓ | ✓ | dilab/omnipay-ipay88 | [Xu Ding](https://github.com/dilab)
[Ikajo](https://github.com/hiqdev/omnipay-ikajo) | ✓ | ✓ | hiqdev/omnipay-ikajo | [HiQDev](https://github.com/hiqdev)
[InterKassa](https://github.com/hiqdev/omnipay-interkassa) | ✓ | ✓ | hiqdev/omnipay-interkassa | [HiQDev](https://github.com/hiqdev)
[InovioPay](https://github.com/mvestil/omnipay-inoviopay) | ✓ | ✓ | mvestil/omnipay-inoviopay | [Mark Vestil](https://github.com/mvestil)
[Klarna Checkout](https://github.com/MyOnlineStore/omnipay-klarna-checkout) | ✓ | ✓ | myonlinestore/omnipay-klarna-checkout | [MyOnlineStore](https://github.com/MyOnlineStore)
[Luminor Gateway](https://github.com/DeH4eG/omnipay-luminor) | - | ✓ | deh4eg/omnipay-luminor | [Denis Smolakov](https://github.com/DeH4eG)
[Midtrans](https://github.com/dilab/omnipay-midtrans) | ✓ | ✓ | dilab/omnipay-midtrans | [Xu Ding](https://github.com/dilab)
[MercadoPago](https://github.com/lucassmacedo/omnipay-mercadopago) | - | ✓ | lucassmacedo/omnipay-mercadopago | [Lucas Macedo](https://github.com/lucassmacedo)
[Magnius](https://github.com/fruitcake/omnipay-magnius) | - | ✓ | fruitcake/omnipay-magnius | [Fruitcake](https://github.com/fruitcake)
[MTNCAM Mobile Money](https://github.com/larrytech7/omnipay-momocm) | ✓ | ✓ | larrytech7/omnipay-momocm | [Akah Harvey](https://github.com/larrytech7)
[MoMo](https://github.com/phpviet/omnipay-momo) | - | ✓ | phpviet/omnipay-momo | [PHPViet](https://github.com/phpviet)
[Moneris](https://github.com/unoapp-dev/omnipay-moneris) | - | ✓ | unoapp-dev/omnipay-moneris | [UNOapp Dev](https://github.com/unoapp-dev)
[GiroCheckout](https://github.com/academe/Omnipay-GiroCheckout) | ✓ | ✓ | academe/omnipay-girocheckout | [Jason Judge](https://github.com/judgej)
[MyFatoorah](https://github.com/my-fatoorah/omnipay-myfatoorah) | - | ✓ | myfatoorah/omnipay | [MyFatoorah Plugins Team](https://github.com/my-fatoorah)
[National Australia Bank (NAB) Transact](https://github.com/sudiptpa/omnipay-nabtransact) | ✓ | ✓ | sudiptpa/omnipay-nabtransact | [Sujip Thapa](https://github.com/sudiptpa)
[NestPay (EST)](https://github.com/uskur/omnipay-nestpay) | - | ✓ | uskur/omnipay-nestpay | [Uskur](https://github.com/uskur)
[Nocks](https://github.com/nocksapp/checkout-omnipay) | ✓ | ✓ | nocksapp/omnipay-nocks | [Nocks](https://github.com/nocksapp)
[Nuvei](https://github.com/diversifiedtech/omnipay-nuvei) | - | ✓ | nmc9/omnipay-nuvei | [DiversifiedTech](https://github.com/diversifiedtech)
[OkPay](https://github.com/hiqdev/omnipay-okpay) | ✓ | ✓ | hiqdev/omnipay-okpay | [HiQDev](https://github.com/hiqdev)
[OnePay](https://github.com/dilab/omnipay-onepay) | ✓ | ✓ | dilab/omnipay-onepay | [Xu Ding](https://github.com/dilab)
[Openpay Australia](https://github.com/sudiptpa/openpay) | ✓ | ✓ | sudiptpa/omnipay-openpay | [Sujip Thapa](https://github.com/sudiptpa)
[Oppwa](https://github.com/vdbelt/omnipay-oppwa) | ✓ | ✓ | vdbelt/omnipay-oppwa | [Martin van de Belt](https://github.com/vdbelt)
[PAY. (Pay.nl & Pay.be)](https://github.com/paynl/omnipay-paynl) | ✓ | ✓ | paynl/omnipay-paynl | [Andy Pieters](https://github.com/andypieters)
[PayMongo](https://github.com/oozman/omnipay-paymongo) | - | ✓ | oozman/omnipay-paymongo | [Oozman](https://github.com/oozman)
[Payoo](https://github.com/dilab/omnipay-payoo) | ✓ | ✓ | dilab/omnipay-payoo | [Xu Ding](https://github.com/dilab)
[PaymentgateRu](https://github.com/pinguinjkeke/omnipay-paymentgateru) | ✓ | ✓ | pinguinjkeke/omnipay-paymentgateru | [Alexander Avakov](https://github.com/pinguinjkeke)
[Paynow](https://github.com/pay-now/omnipay-paynow) | - | ✓ | pay-now/omnipay-paynow | [Paynow](https://github.com/pay-now)
[PAYONE](https://github.com/academe/omnipay-payone) | ✓ | ✓ | academe/omnipay-payone | [Jason Judge](https://github.com/judgej)
[Paysafecard](https://github.com/worldstream-labs/omnipay-paysafecard) | - | ✓ | worldstream-labs/omnipay-paysafecard | [Worldstream](https://github.com/worldstream-labs)
[Paysafe Payment Hub (Neteller)](https://github.com/worldstream-labs/omnipay-paysafe-payment-hub) | - | ✓ | worldstream-labs/omnipay-paysafe-payment-hub | [Worldstream](https://github.com/worldstream-labs)
[Paysera](https://github.com/semyonchetvertnyh/omnipay-paysera) | - | ✓ | semyonchetvertnyh/omnipay-paysera | [Semyon Chetvertnyh](https://github.com/semyonchetvertnyh)
[Paxum](https://github.com/hiqdev/omnipay-paxum) | ✓ | ✓ | hiqdev/omnipay-paxum | [HiQDev](https://github.com/hiqdev)
[Pelecard](https://github.com/Uskur/omnipay-pelecard) | ✓ | ✓ | uskur/omnipay-pelecard | [Uskur](https://github.com/Uskur)
[Qiwi](https://github.com/hiqdev/omnipay-qiwi) | ✓ | ✓ | hiqdev/omnipay-qiwi | [HiQDev](https://github.com/hiqdev)
[RoboKassa](https://github.com/hiqdev/omnipay-robokassa) | ✓ | ✓ | hiqdev/omnipay-robokassa | [HiQDev](https://github.com/hiqdev)
[RocketGate](https://github.com/mvestil/omnipay-rocketgate) | ✓ | ✓ | mvestil/omnipay-rocketgate | [Mark Vestil](https://github.com/mvestil)
[Sberbank](https://github.com/AndrewNovikof/omnipay-sberbank) | - | ✓ | andrewnovikof/omnipay-sberbank | [Andrew Novikov](https://github.com/AndrewNovikof)
[Sisow](https://github.com/fruitcake/omnipay-sisow) | ✓ | ✓ | fruitcakestudio/omnipay-sisow | [Fruitcake](https://github.com/fruitcake)
[ToyyibPay](https://github.com/sitehandy/omnipay-toyyibpay) | - | ✓ | sitehandy/omnipay-toyyibpay | [Amirol Zolkifli](https://github.com/sitehandy)
[VR Payment](https://github.com/antibodies-online/omnipay-vr-payment) | - | ✓ | antibodies-online/omnipay-vr-payment | [antibodies-online](https://github.com/antibodies-online)
[WebMoney](https://github.com/dercoder/omnipay-webmoney) | ✓ | ✓ | dercoder/omnipay-webmoney | [Alexander Fedra](https://github.com/dercoder)
[Wirecard](https://github.com/igaponov/omnipay-wirecard) | ✓ | ✓ | igaponov/omnipay-wirecard | [Igor Gaponov](https://github.com/igaponov)
[Worldpay XML Hosted Corporate Gateway](https://github.com/catharsisjelly/omnipay-worldpay-cg-hosted) | ✓ | ✓ | catharsisjelly/omnipay-worldpay-cg-hosted | [Chris Lock](https://github.com/catharsisjelly)
[Yandex.Kassa](https://github.com/hiqdev/omnipay-yandex-kassa) | ✓ | ✓ | hiqdev/omnipay-yandex-kassa | [HiQDev](https://github.com/hiqdev)
[Yandex.Money for P2P payments](https://github.com/hiqdev/omnipay-yandexmoney) | ✓ | ✓ | hiqdev/omnipay-yandexmoney | [HiQDev](https://github.com/hiqdev)
[Yekpay](https://github.com/nekofar/omnipay-yekpay) | - | ✓ | nekofar/omnipay-yekpay | [Milad Nekofar](https://github.com/nekofar)
[ZarinPal](https://github.com/nekofar/omnipay-zarinpal) | - | ✓ | nekofar/omnipay-zarinpal | [Milad Nekofar](https://github.com/nekofar)

### 无法支持

Gateway | 2.x | 3.x | Composer Package | Maintainer
--- | --- | --- | --- | ---
[2Checkout](https://github.com/thephpleague/omnipay-2checkout) | ✓ | - | omnipay/2checkout | [Omnipay](https://github.com/thephpleague/omnipay)
[2Checkout Improved](https://github.com/collizo4sky/omnipay-2checkout) | ✓ | - | collizo4sky/omnipay-2checkout | [Agbonghama Collins](https://github.com/collizo4sky)
[Acapture (PayVision)](https://github.com/queueup-dev/omnipay-acapture) | ✓ | - | qup/omnipay-acapture | [Niels de Vries](https://github.com/niels-qup)
[Agms](https://github.com/agmscode/omnipay-agms) | ✓ | - | agmscode/omnipay-agms | [Maanas Royy](https://github.com/maanas)
[Allied Wallet](https://github.com/delatbabel/omnipay-alliedwallet) | ✓ | - | delatbabel/omnipay-alliedwallet | [Del](https://github.com/delatbabel)
[Barclays ePDQ](https://github.com/digitickets/omnipay-barclays-epdq) | ✓ | - | digitickets/omnipay-barclays-epdq | [DigiTickets](https://github.com/digitickets)
[Beanstream](https://github.com/lemonstand/omnipay-beanstream) | ✓ | - | lemonstand/omnipay-beanstream | [LemonStand](https://github.com/lemonstand)
[BKM Express](https://github.com/yasinkuyu/omnipay-bkm) | ✓ | - | yasinkuyu/omnipay-bkm | [Yasin Kuyu](https://github.com/yasinkuyu)
[BlueSnap](https://github.com/vimeo/omnipay-bluesnap) | ✓ | - | vimeo/omnipay-bluesnap | [Vimeo](https://github.com/vimeo)
[Buckaroo](https://github.com/thephpleague/omnipay-buckaroo) | ✓ | - | omnipay/buckaroo | [Omnipay](https://github.com/thephpleague/omnipay)
[CardGate](https://github.com/cardgate/omnipay-cardgate) | ✓ | - | cardgate/omnipay-cardgate | [CardGate](https://github.com/cardgate)
[CardSave](https://github.com/thephpleague/omnipay-cardsave) | ✓ | - | omnipay/cardsave | [Omnipay](https://github.com/thephpleague/omnipay)
[Checkout.com](https://github.com/fotografde/omnipay-checkoutcom) | ✓ | - | fotografde/checkoutcom | [fotograf.de](https://github.com/fotografde)
[CloudBanking](https://github.com/spsingh/omnipay-cloudbanking) | ✓ | - | cloudbanking/omnipay-cloudbanking | [Cloudbanking](http://cloudbanking.com.au/)
[Coinbase](https://github.com/thephpleague/omnipay-coinbase) | ✓ | - | omnipay/coinbase | [Omnipay](https://github.com/thephpleague/omnipay)
[CoinGate](https://github.com/coingate/omnipay-coingate) | ✓ | - | coingate/omnipay-coingate | [CoinGate](https://github.com/coingate)
[Creditcall](https://github.com/meebio/omnipay-creditcall) | ✓ | - | meebio/omnipay-creditcall | [John Jablonski](https://github.com/jan-j)
[CSOB](https://github.com/bileto/omnipay-csob) (GP WebPay) | ✓ | - | bileto/omnipay-csob |
[Cybersource SOAP](https://github.com/Klinche/omnipay-cybersource-soap) | ✓ | - | dabsquared/omnipay-cybersource-soap | [DABSquared](https://github.com/DABSquared)
[DataCash](https://github.com/digitickets/omnipay-datacash) | ✓ | - | digitickets/omnipay-datacash | [DigiTickets](https://github.com/digitickets)
[Datatrans](https://github.com/w-vision/omnipay-datatrans) | ✓ | - | w-vision/datatrans | [Dominik Pfaffenbauer](https://github.com/dpfaffenbauer)
[ecoPayz](https://github.com/dercoder/omnipay-ecopayz) | ✓ | - | dercoder/omnipay-ecopayz | [Alexander Fedra](https://github.com/dercoder)
[EgopayRu](https://github.com/pinguinjkeke/omnipay-egopaymentru) | ✓ | - | pinguinjkeke/omnipay-egopaymentru | [Alexander Avakov](https://github.com/pinguinjkeke)
[Fasapay](https://github.com/andreas22/omnipay-fasapay) | ✓ | - | andreas22/omnipay-fasapay | [Andreas Christodoulou](https://github.com/andreas22)
[Fat Zebra](https://github.com/delatbabel/omnipay-fatzebra) | ✓ | - | delatbabel/omnipay-fatzebra | [Del](https://github.com/delatbabel)
[First Data](https://github.com/thephpleague/omnipay-firstdata) | ✓ | - | omnipay/firstdata | [OmniPay](https://github.com/thephpleague/omnipay)
[Flo2cash](https://github.com/guisea/omnipay-flo2cash) | ✓ | - | guisea/omnipay-flo2cash | [Aaron Guise](https://github.com/guisea)
[Free / Zero Amount](https://github.com/colinodell/omnipay-zero) | ✓ | - | colinodell/omnipay-zero | [Colin O'Dell](https://github.com/colinodell)
[Globalcloudpay](https://github.com/dercoder/omnipay-globalcloudpay) | ✓ | - | dercoder/omnipay-globalcloudpay | [Alexander Fedra](https://github.com/dercoder)
[GoCardless](https://github.com/thephpleague/omnipay-gocardless) | ✓ | - | omnipay/gocardless | [Del](https://github.com/delatbabel)
[GoPay](https://github.com/bileto/omnipay-gopay) | ✓ | - | bileto/omnipay-gopay |
[GovPayNet](https://github.com/flexcoders/omnipay-govpaynet) | ✓ | - | omnipay/omnipay-govpaynet | [FlexCoders](https://github.com/flexcoders)
[GVP (Garanti)](https://github.com/yasinkuyu/omnipay-gvp) | ✓ | - | yasinkuyu/omnipay-gvp | [Yasin Kuyu](https://github.com/yasinkuyu)
[Helcim](https://github.com/academe/omnipay-helcim) | ✓ | - | academe/omnipay-helcim | [Jason Judge](https://github.com/judgej)
[IfthenPay](https://github.com/ifthenpay/omnipay-ifthenpay) | ✓ | - | ifthenpay/omnipay-ifthenpay | [Rafael Almeida](https://github.com/rafaelcpalmeida)
[Iyzico](https://github.com/yasinkuyu/omnipay-iyzico) | ✓ | - | yasinkuyu/omnipay-iyzico | [Yasin Kuyu](https://github.com/yasinkuyu)
[Judo Pay](https://github.com/Transportersio/omnipay-judopay) | ✓ | - | transportersio/omnipay-judopay | [Transporters.io](https://github.com/Transportersio)
[Laybuy](https://github.com/mediabeastnz/omnipay-laybuy) | ✓ | - | mediabeastnz/omnipay-laybuy | [Myles Derham](https://github.com/mediabeastnz)
[Komerci (Rede, former RedeCard)](https://github.com/byjg/omnipay-komerci) | ✓ | - | byjg/omnipay-komerci | [João Gilberto Magalhães](https://github.com/byjg)
[Komoju](https://github.com/dannyvink/omnipay-komoju) | ✓ | - | vink/omnipay-komoju | [Danny Vink](https://github.com/dannyvink)
[Manual](https://github.com/thephpleague/omnipay-manual) | ✓ | - | omnipay/manual | [Del](https://github.com/delatbabel)
[Migs](https://github.com/thephpleague/omnipay-migs) | ✓ | - | omnipay/migs | [Omnipay](https://github.com/thephpleague/omnipay)
[Mpesa](https://github.com/wasksofts/omnipay-mpesa) | ✓ | - | wasksofts/omnipay-mpesa | [wasksofts](https://github.com/wasksofts/omnipay-mpesa)
[MOLPay](https://github.com/leesiongchan/omnipay-molpay) | ✓ | - | leesiongchan/molpay | [Lee Siong Chan](https://github.com/leesiongchan)
[MultiCards](https://github.com/incube8/omnipay-multicards) | ✓ | - | incube8/omnipay-multicards | [Del](https://github.com/delatbabel)
[MultiSafepay](https://github.com/thephpleague/omnipay-multisafepay) | ✓ | - | omnipay/multisafepay | [Alexander Deruwe](https://github.com/aderuwe)
[MyCard](https://github.com/xxtime/omnipay-mycard) | ✓ | - | xxtime/omnipay-mycard | [Joe Chu](https://github.com/xxtime)
[NestPay (EST)](https://github.com/yasinkuyu/omnipay-nestpay) | ✓ | - | yasinkuyu/omnipay-nestpay | [Yasin Kuyu](https://github.com/yasinkuyu)
[Netaxept (BBS)](https://github.com/thephpleague/omnipay-netaxept) | ✓ | - | omnipay/netaxept | [Omnipay](https://github.com/thephpleague/omnipay)
[Netbanx](https://github.com/thephpleague/omnipay-netbanx) | ✓ | - | omnipay/netbanx | [Maks Rafalko](https://github.com/borNfreee)
[Neteller](https://github.com/dercoder/omnipay-neteller) | ✓ | - | dercoder/omnipay-neteller | [Alexander Fedra](https://github.com/dercoder)
[NetPay](https://github.com/netpay/omnipay-netpay) | ✓ | - | netpay/omnipay-netpay | [NetPay](https://github.com/netpay)
[Network Merchants Inc. (NMI)](https://github.com/mfauveau/omnipay-nmi) | ✓ | - | mfauveau/omnipay-nmi | [Matthieu Fauveau](https://github.com/mfauveau)
[Pacnet](https://github.com/mfauveau/omnipay-pacnet) | ✓ | - | mfauveau/omnipay-pacnet | [Matthieu Fauveau](https://github.com/mfauveau)
[Pagar.me](https://github.com/descubraomundo/omnipay-pagarme) | ✓ | - | descubraomundo/omnipay-pagarme | [Descubra o Mundo](https://github.com/descubraomundo)
[Paratika (Asseco)](https://github.com/yasinkuyu/omnipay-paratika) | ✓ | - | yasinkuyu/omnipay-paratika | [Yasin Kuyu](https://github.com/yasinkuyu)
[PayFast](https://github.com/thephpleague/omnipay-payfast) | ✓ | - | omnipay/payfast | [Omnipay](https://github.com/thephpleague/omnipay)
[Payflow](https://github.com/thephpleague/omnipay-payflow) | ✓ | - | omnipay/payflow | [Del](https://github.com/delatbabel)
[PaymentExpress / DPS (A2A)](https://github.com/onlinesid/omnipay-paymentexpress-a2a) | ✓ | - | onlinesid/omnipay-paymentexpress-a2a | [Sid](https://github.com/onlinesid)
[PaymentSense](https://github.com/digitickets/omnipay-paymentsense) | ✓ | - | digitickets/omnipay-paymentsense | [DigiTickets](https://github.com/digitickets)
[PayPro](https://github.com/payproNL/omnipay-paypro) | ✓ | - | paypronl/omnipay-paypro | [Fruitcake](https://github.com/fruitcake)
[Paysafecard](https://github.com/dercoder/omnipay-paysafecard) | ✓ | - | dercoder/omnipay-paysafecard | [Alexander Fedra](https://github.com/dercoder)
[Paysera](https://github.com/povils/omnipay-paysera) | ✓ | - | povils/omnipay-paysera | [Povils](https://github.com/povils)
[PaySimple](https://github.com/dranes/omnipay-paysimple) | ✓ | - | dranes/omnipay-paysimple | [Dranes](https://github.com/dranes)
[PaySsion](https://github.com/InkedCurtis/omnipay-payssion) | ✓ | - | inkedcurtis/omnipay-payssion | [Curtis](https://github.com/inkedcurtis)
[PayTrace](https://github.com/iddqdidkfa/omnipay-paytrace) | ✓ | - | softcommerce/omnipay-paytrace | [Oleg Ilyushyn](https://github.com/iddqdidkfa)
[PayU](https://github.com/bileto/omnipay-payu) | ✓ | - | bileto/omnipay-payu |
[PayZen](https://github.com/ubitransports/omnipay-payzen) | ✓ | - | ubitransports/omnipay-payzen | [Ubitransport](https://github.com/ubitransports)
[Pin Payments](https://github.com/thephpleague/omnipay-pin) | ✓ | - | omnipay/pin | [Del](https://github.com/delatbabel)
[POLi](https://github.com/burnbright/omnipay-poli) | ✓ | - | burnbright/omnipay-poli | [Sid](https://github.com/onlinesid)
[Portmanat](https://github.com/dercoder/omnipay-portmanat) | ✓ | - | dercoder/omnipay-portmanat | [Alexander Fedra](https://github.com/dercoder)
[Posnet](https://github.com/yasinkuyu/omnipay-posnet) | ✓ | - | yasinkuyu/omnipay-posnet | [Yasin Kuyu](https://github.com/yasinkuyu)
[Postfinance](https://github.com/bummzack/omnipay-postfinance) | ✓ | - | bummzack/omnipay-postfinance | [Roman Schmid](https://github.com/bummzack)
[Quickpay](https://github.com/NobrainerWeb/omnipay-quickpay) | ✓ | - | nobrainerweb/omnipay-quickpay | [Nobrainer Web](https://github.com/NobrainerWeb)
[Rabobank](https://github.com/thephpleague/omnipay-rabobank) | ✓ | - | omnipay/rabobank | [Barry vd. Heuvel](https://github.com/barryvdh)
[Razorpay](https://github.com/razorpay/omnipay-razorpay) | ✓ | - |  razorpay/omnipay-razorpay  | [razorpay](https://github.com/razorpay)
[Realex](https://github.com/digitickets/omnipay-realex) | ✓ | - | digitickets/omnipay-realex | [DigiTickets](https://github.com/digitickets)
[RedSys](https://github.com/jsampedro77/sermepa-omnipay) | ✓ | - | nazka/sermepa-omnipay | [Javier Sampedro](https://github.com/jsampedro77)
[RentMoola](https://github.com/rentmoola/omnipay-rentmoola) | ✓ | - | rentmoola/omnipay-rentmoola | [Geoff Shaw](https://github.com/Shawg)
[SecPay](https://github.com/justinbusschau/omnipay-secpay) | ✓ | - | justinbusschau/omnipay-secpay | [Justin Busschau](https://github.com/justinbusschau)
[Secure Trading](https://github.com/meebio/omnipay-secure-trading) | ✓ | - | meebio/omnipay-secure-trading | [John Jablonski](https://github.com/jan-j)
[Skrill](https://github.com/alfaproject/omnipay-skrill) | ✓ | - | alfaproject/omnipay-skrill | [João Dias](https://github.com/alfaproject)
[Sofort](https://github.com/aimeoscom/omnipay-sofort) | ✓ | - | aimeoscom/omnipay-sofort | [Aimeos GmbH](https://github.com/aimeoscom)
[Spreedly](https://github.com/gregoriohc/omnipay-spreedly) | ✓ | - | gregoriohc/omnipay-spreedly | [Gregorio Hernández Caso](https://github.com/gregoriohc)
[TargetPay](https://github.com/thephpleague/omnipay-targetpay) | ✓ | - | omnipay/targetpay | [Alexander Deruwe](https://github.com/aderuwe)
[TatraBank](https://github.com/bileto/omnipay-tatrabank) | ✓ | - | omnipay-tatrabank |
[Tpay](https://github.com/tpay-com/omnipay-tpay) | ✓ | - | omnipay/tpay | [Tpay.com](https://github.com/tpay-com)
[Vantiv](https://github.com/lemonstand/omnipay-vantiv) | ✓ | - | lemonstand/omnipay-vantiv | [LemonStand](https://github.com/lemonstand)
[Veritrans](https://github.com/andylibrian/omnipay-veritrans) | ✓ | - | andylibrian/omnipay-veritrans | [Andy Librian](https://github.com/andylibrian)
[Vindicia](https://github.com/vimeo/omnipay-vindicia) | ✓ | - | vimeo/omnipay-vindicia | [Vimeo](https://github.com/vimeo)
[VivaPayments](https://github.com/delatbabel/omnipay-vivapayments) | ✓ | - | delatbabel/omnipay-vivapayments | [Del](https://github.com/delatbabel)
[WeChat](https://github.com/labs7in0/omnipay-wechat) | ✓ | - | labs7in0/omnipay-wechat | [7IN0's Labs](https://github.com/labs7in0)
[WePay](https://github.com/collizo4sky/omnipay-wepay) | ✓ | - | collizo4sky/omnipay-wepay | [Agbonghama Collins](https://github.com/collizo4sky)
[Wirecard](https://github.com/academe/omnipay-wirecard) | ✓ | - | academe/omnipay-wirecard | [Jason Judge](https://github.com/judgej)
[Worldpay XML Direct Corporate Gateway](https://github.com/teaandcode/omnipay-worldpay-xml) | ✓ | - | teaandcode/omnipay-worldpay-xml | [Dave Nash](https://github.com/teaandcode)
[Yandex.Money](https://github.com/yandex-money/yandex-money-cms-omnipay) | ✓ | - | yandexmoney/omnipay | [Roman Ananyev](https://github.com/aTastyCookie/)
