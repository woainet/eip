# Set the Multi-EIP to ENI mode {#task_268616 .task}

This topic describes how to set the Multi-EIP to ENI mode. When you associate multiple Elastic IP Addresses \(EIPs\) with a secondary Elastic Network Interface \(ENI\), you can select the **Multi-EIP to ENI Mode**. In this mode, the private and public IP addresses of the ENI are available at the same time. You can see the EIPs in the network interface information of the operating system.

Make sure that the following conditions are met before you set the Multi-EIP to ENI mode.

-   A secondary ENI is created. For more information, see [Create an ENI](../../../../reseller.en-US/Network/Elastic Network Interfaces/Create an ENI.md#).
-   The secondary ENI is not associated with any EIP in the NAT or cut-through mode.

    If the secondary ENI is already associated with an EIP, disassociate the EIP first. For more information, see [Disassociate an EIP](reseller.en-US/User Guide/Disassociate an EIP from a cloud instance.md#).


EIPs are a type of NAT IP address. Because the public IP address in the NAT mode exists in the NAT Gateway and is not on the network interface of the ECS instance, you cannot see the public IP address in the operating system and can only see the private IP address. This complicates the operation and maintenance, and the relationship between network interfaces/servers and public IP addresses must be maintained manually. Additionally, when an EIP is deployed as a NAT ALG \(NAT application layer gateway\), protocols such as H.323, SIP, DNS, and RTSP are not supported.

The **Multi-EIP to ENI Mode** makes the EIP visible on the network interface and solves the preceding problems. In the Multi-EIP to ENI mode:

-   The intranet function of the secondary ENI is still available.
-   The EIPs are visible to the ENI. After the operating system is configured with a static IP address, you can run the ifconfig or ipconfig command to obtain the public IP address of the ENI.
-   The EIP supports all IP protocol types, including FTP, H.323, SIP, DNS, RTSP, and TFTP.

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, choose **Elastic IP Addresses**.
3.  Select the region of the target EIP. 

    **Note:** Currently, the Multi-EIP to ENI mode is supported only in the China \(Zhangjiakou\), Singapore, Germany \(Frankfurt\), India \(Mumbai\), and UK \(London\) regions.

4.  On the Elastic IP Addresses page, find the target EIP and click **Bind** in the **Actions** column.
5.  On the Bind Elastic IP Address page, complete the following configurations, and then click **OK**. 

    |Configuration|Required?|Description|
    |-------------|---------|-----------|
    |**Instance Type**|Yes|Select **Secondary ENI**.|
    |**Resource Group**|No|Select the resource group to which the EIP belongs.|
    |**Mode**|No|Select **Multi-EIP to ENI Mode**.|
    |**Secondary ENI**|Yes|Select the secondary ENI to be associated with the EIP.|

    ![Associate an EIP with a secondary ENI](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/221990/156405168747675_en-US.png)

6.  Repeat the preceding steps to associate multiple EIPs with the secondary ENI.
7.  Return to the EIP list page and click the ID of the associated ENI. 

    ![View the ENI associated with the EIP](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65386/156405168733382_en-US.png)

8.  On the Network Interfaces page, find the target ENI and click **Bind to Instance** to associate the ENI with an ECS instance. 

    **Note:** 

    -   When you associate an ENI that is associated with multiple EIPs in the Multi-EIP to ENI mode with an ECS instance, the ECS instance must be of the following specifications: ecs.c5-618, ecs.d1ne, ecs.db11-se1ne, ecs.ebma1, ecs.ebmc4, ecs.ebmg4, ecs.ebmg5, ecs.ebmg5ne, ecs.ebmgn5i, ecs.ebmgn5t, ecs.ebmhfg4, ecs.ebmhfg5, ecs.ebmi2, ecs.ebmi3, ecs.ebmr4, ecs.ebmr5, ecs.elmd1ne, ecs.elmdb, ecs.f1, ecs.f2, ecs.g5-618, ecs.gn3, ecs.gn5d, ecs.gn5i, ecs.gn5t, ecs.gn6p, ecs.gn6v, ecs.i2, ecs.r1, ecs.re4, ecs.re4e, ecs.sccg5, ecs.sccgn6, ecs.scch5, ecs.x1.i2, ecs.x1.i5, ecs.x1.i6, ecs.x1.i8, ecs.g5, ecs.c5, ecs.r5, ecs.t5, ecs.sn2ne, ecs.se1ne, and ecs.sn1ne. For more information, see [Instance type families](../../../../reseller.en-US/Instances/Instance type families.md#).
    -   After you set the Multi-EIP to ENI mode, you must enable the DHCP function of the ECS instance with which the ENI is associated to make the Multi-EIP to ENI mode take effect.
9.  Call DescribeEipGatewayInfo to obtain the gateway addresses and subnet masks of the EIPs. For more information, see [DescribeEipGatewayInfo](../../../../reseller.en-US/API reference/EIP/DescribeEipGatewayInfo.md#).
10. Log on to the ECS instance and configure multiple EIPs for the ECS instance. For more information, see [Configure an EIP for a Windows instance](../../../../reseller.en-US/Network/Elastic Network Interfaces/Assign a secondary private IP address.md#section_y4b_krk_ggb) and [Configure an EIP for a Linux instance](../../../../reseller.en-US/Network/Elastic Network Interfaces/Assign a secondary private IP address.md#section_b2x_hlb_3gb). 

    **Note:** When you configure EIPs for the ECS instance, change the secondary private IP addresses to EIP addresses and change the gateway addresses and subnet masks of the private IP addresses to the gateway addresses and subnet masks of the EIPs.

    After configuring EIPs, you can run the ifconfig or ipconfig command to view the configured EIPs.

11. \(Optional\) After setting the Multi-EIP to ENI mode, you can test the network connectivity. For more information, see [Test network connectivity](../../../../reseller.en-US/Best practices/Associate multiple EIPs with an ENI in the NAT mode.md#section_6l6_t3r_azk).

