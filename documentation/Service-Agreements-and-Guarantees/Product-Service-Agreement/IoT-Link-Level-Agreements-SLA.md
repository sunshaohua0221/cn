本服务等级协议（Service Level Agreement，简称 “SLA”）规定了京东云向客户提供的物联网卡服务的可用性等级指标及赔偿方案，协议自2019年9月25日起生效。

**1. 定义**

**服务周期：**一个服务周期为一个自然月，客户申请物联网卡业务当月，以申请激活之日起至（移动、电信）月末，（联通当月26日）为一个服务周期。

**服务不可用定义：**客户每一次调用发起物联网卡服务的API接口（不包括物联卡设备信息提交（DoIotPostImei）、物联网卡激活消息通知、物联网卡停复机通知、物联网卡实名认证通知）尝试失败（system_error），则视为该次调用该服务不可用。

**服务周期总调用次数：**按照每月每周七（7）天每天二十四（24）小时计算，客户申请物联网卡服务当月，以申请之日起至申请月月末按照前述标准累计计算的调用次数作为服务周期总次数。

**服务周期服务费用：**客户在一个自然月中就物联网卡服务所支付的实际服务费用总额。服务对象：所有使用京东云通信物联网卡服务POP接口的用户（不包括TOP接口的用户）。

**2. 服务可用性计算方式**

**服务可用性=( (服务周期总调用次数-服务周期不可用次数)/服务周期总调用次数) × 100%物联网卡服务可用性不低于99%，如服务未达到上述可用性承诺，客户申请赔偿。**

**2.1服务指标承诺**

| 服务指标   | 承诺指标 |
| ---------- | -------- |
| 服务可用性 | 99%      |

 

2.2 如物联网卡服务未达到上述服务可用性承诺，客户可以根据本协议第3.1条约定获得赔偿。赔偿范围**不包括**以下原因所导致的服务不可用造成的未达到上述服务指标承诺：

（1）京东云预先通知客户后进行系统维护所引起的，包括割接、维修、升级和模拟故障演练；

（2）任何京东云所属设备以外的网络、设备故障或配置调整引起的；

（3）客户的应用程序受到黑客攻击而引起的；

（4）客户使用、维护、保密不当致使数据丢失、泄露所引起的；

（5）客户的疏忽或由客户授权的操作所引起的；

（6）客户未遵循京东云通信产品使用文档或使用建议引起的；

（7）京东云公告提前告知客户由于重大活动或者促销引起的；

（8）客户由于信控、流控、信息安全管控等违反平台规则引起的；

（9）任何涉及黄赌毒、党政军、诈骗等非法改为物联网内容引起的；

（10）因国家工信部、信管局、运营商等管控引起的；

（11）客户经由特殊商品或档位可见、测试和邀约下单，购买非公开试运营的产品功能及权限的；

（12）客户购买套餐为京东云通信转售，而京东云通信封装的；

（13）其他不可抗力引起的。

**3.赔偿方案**

**3.1 赔偿标准**

根据客户某一京东云账号下物联网卡服务可用性指标，按照以下列表标准进行赔偿。客户某一京东云账号下物联网卡服务月度赔偿金额不可叠加，若同时满足两项赔偿条件，以最高赔付金额为准，赔付金额为该京东云账号下物联网卡通知产品当月实际账单金额的对应比例。

| 指标类型                  | 服务指标                     | 赔偿代金券金额     |
| ------------------------- | ---------------------------- | ------------------ |
| 服务可用性                | 低于 99. 5% 但等于或高于 95% | 月度服务费用的 10% |
| 低于 95% 但等于或高于 90% | 月度服务费用的 30%           |                    |
| 低于 90%                  | 月度服务费用的 50%           |                    |

 

**3.2 赔偿申请时限**

客户可以在每月第五（5）个工作日后对上一服务周期没有达到服务指标的服务提出赔偿申请，赔偿申请必须在服务可用性没有达到可用性的服务周期结束后两（2）个月内提出，否则超出申请时限的赔偿申请将不被受理。如：2019年1月没有达到服务指标的，则客户最迟需要在2019年3月31日前提出赔偿。

**4. 其他**

京东云有权对本SLA条款作出修改。如本SLA条款有任何修改，京东云将提前30天以网站公示或发送邮件的方式通知您。如您不同意京东云对SLA所做的修改，您有权停止使用物联网卡服务，如您继续使用，则视为您接受修改后的SLA。