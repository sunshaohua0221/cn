
# 简介 #
  欢迎使用京东云开发者Node.js工具套件（Node.js SDK）。使用京东云Node.js SDK，您无需复杂编程就可以访问京东云提供的各种服务。 

  为了方便您理解SDK中的一些概念和参数的含义，使用SDK前建议您先查看[京东云OpenAPI使用入门](http://www.jdcloud.com/help/detail/355/isCatalog/0)。要了解每个API的具体参数和含义，请参考程序注释或参考OpenAPI&SDK下具体产品线的API文档。



# 环境准备 #
 1.京东云Node.js SDK适用于Node.js 8.6.0及以上，npm 5.6.0及以上。

 2.在开始调用京东云open API之前，需提前在京东云用户中心账户管理下的[AccessKey管理页面](https://uc.jdcloud.com/accesskey/index)申请accesskey和secretKey密钥对（简称AK/SK）。AK/SK信息请妥善保管，如果遗失可能会造成非法用户使用此信息操作您在云上的资源，给你造成数据和财产损失。



# SDK使用方法 #
建议使用npm安装京东云Node.js SDK，如下所示： 

npm install jdcloud-sdk-js

 

您还可以下载sdk源代码自行使用，[源代码地址](https://github.com/jdcloud-api/jdcloud-sdk-nodejs)。

 

SDK使用中的任何问题，欢迎您在[SDK使用问题反馈页面](https://github.com/jdcloud-api/jdcloud-sdk-nodejs/issues)交流。



注意：京东云并没有提供其他下载方式，请务必使用上述官方下载方式！

 

# 调用SDK #

## 两种引用方式 ##
	var JDCloud = require('jdcloud-sdk-js');

这种引用方式会加载所有的可用的services



	var NC = require('jdcloud-sdk-js/services/nativecontainer');

这种引用方式只会加载用到的service，此时仍然可以使用var JDCloud = require('jdcloud-sdk-js/global')来引用JDCloud对象

## 配置方法  ##

对JDCloud的配置为通用配置，所有services共享配置:

	JDCloud.config.update({//*配置项/*/});

对某个service的配置会覆盖通用配置：

	var NC = require('jdcloud-sdk-js/services/nativecontainer'); 
	var nc = new NATIVECONTAINER({//*配置项/*/});


## 配置项 ##

	let config = { 
		credentials: { 
			accessKeyId: global.accessKeyId, secretAccessKey: global.secretAccessKey 
		},
		regionId: 'cn-north-1' //地域信息，某个api调用可以单独传参regionId，如果不传则会使用此配置中的regionId 
	}


## 调用示例 ##

以下是查询单个云主机实例详情的调用示例


###  引用和配置  ###

    var VM = require('jdcloud-sdk-js/services/vm')
    var vm = new VM({
            credentials: {
        accessKeyId: global.accessKeyId,
                secretAccessKey: global.secretAccessKey
    },
    regionId: 'cn-north-1'
    })



### Promise方式调用 ####

	vm.createInstances({
        instanceSpec: {
            instanceType: 'g.s1.micro',
                    az: 'cn-north-1a',
                    imageId: '98d44a0f-88c1-451a-8971-f1f769073b6c',
                    name: 'node-sdk-test',
                    elasticIp: {
                bandwidthMbps: 2, provider: 'BGP'
            },
            primaryNetworkInterface: {
                networkInterface: {
                    subnetId: 'subnet-3dm13k30gh',
                            az: 'cn-north-1a'
                }
            },
            systemDisk: {
                diskCategory: 'local'
            },
            description: 'sdk'
        },
        maxCount: 1
    },'cn-north-1').then(function(data){ // 返回数据处理 data 
    },
    function(e){ // 调用API失败，错误处理 
    })



### callback方式调用 ###

	vm.createInstances({
        instanceSpec: {
            instanceType: 'g.s1.micro',
                    az: 'cn-north-1a',
                    imageId: '98d44a0f-88c1-451a-8971-f1f769073b6c',
                    name: 'node-sdk-test',
                    elasticIp: {
                bandwidthMbps: 2,
                        provider: 'BGP'
            },
            primaryNetworkInterface: {
                networkInterface: {
                    subnetId: 'subnet-3dm13k30gh',
                            az: 'cn-north-1a'
                }
            },
            systemDisk: {
                diskCategory: 'local'
            },
            description: 'sdk'
        },
        maxCount: 1
    },'cn-north-1',
    function(err, data){
        if(err){ // 调用API失败，错误处理 
        } 
		else { // 返回数据处理 data 
        } 
    })

如果需要设置访问点，配置超时,额外请求头等，请参考如下更复杂的例子：

```
    var nc = new NATIVECONTAINER({
        credentials: {
            accessKeyId: global.accessKeyId,
            secretAccessKey: global.secretAccessKey
        },
        endpoint: {
            host: 'nativecontainer.internal.cn-north-1.jdcloud-api.com', //指定非默认Endpoint
            protocol: 'http' //设置使用HTTP而不是HTTPS，vpc专用域名不支持HTTPS
        },
        'x-extra-header': { //指定额外header
            "x-jdcloud-security-token" : "xxx", //要调用开启了MFA操作保护的接口需要传递
            "x-jdcloud-content-sha256" : "xxx", //body过大，希望用此value替代对body进行哈希的过程
            "MyOwn" : "xxx"
        },
        version: {
            nativecontainer: 'v1'
        }
    })
```
    

更多调用示例参考  [SDK使用Demo](https://github.com/jdcloud-api/jdcloud-sdk-nodejs/tree/master/test)

**注意：**

- 京东云并没有提供其他下载方式，请务必使用上述官方下载方式！

- version 的版本号需要使用京东云产品提供的最新版本号。例如：示例中VM所使用的最新版本号可到官方提供的API  [更新历史](../../API/Virtual-Machines/ChangeLog.md)  中查询到。

- 每支云产品都有自己的Client，当调用该产品API时，需使用该产品的Client。例如：使用云主机的VmClient只能调用云主机（Vm）的接口；使用高可用组的AgClient只能调用高可用组（Ag）的接口。

