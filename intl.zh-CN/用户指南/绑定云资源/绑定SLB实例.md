# 绑定SLB实例 {#task_593067 .task}

您可以将弹性公网IP绑定到SLB实例上。SLB实例绑定弹性公网IP后，SLB实例可以转发来自公网的请求。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com)。
2.  在左侧导航栏，单击**弹性公网IP**。
3.  选择弹性公网IP的地域。
4.  在弹性公网IP页面，找到目标弹性公网IP，单击**操作**列下的**绑定**。
5.  在绑定弹性公网IP页面，完成以下配置，然后单击**确定**。 

    |配置|说明|
    |:-|:-|
    |**实例类型**|选择SLB实例。 要绑定的SLB实例必须满足以下条件：

    -   SLB实例的网络类型必须是专有网络。
    -   SLB实例的地域必须和EIP的地域相同。
    -   一个SLB实例只能绑定一个EIP。
 |
    |**SLB实例**|选择要绑定的SLB实例。|


**相关文档**  


[AssociateEipAddress](../../../../intl.zh-CN/API参考/弹性公网IP/AssociateEipAddress.md#)

