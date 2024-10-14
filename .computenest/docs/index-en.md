<h1> Rapid deployment of the ChatGPT-on-WeChat computing nest </h1>

<blockquote>
    <p><strong> Disclaimer </strong>: This service is provided by a third party. We try our best to ensure its security,
        accuracy and reliability, but we cannot guarantee that it is completely free from failure, interruption, error
        or attack. Therefore, the company hereby declares that it makes no representations, warranties or commitments
        regarding the content, accuracy, completeness, reliability, suitability and timeliness of the Service and is not
        liable for any direct or indirect loss or damage arising from your use of the Service; for third-party websites,
        applications, products and services that you access through the Service, do not assume any responsibility for
        its content, accuracy, completeness, reliability, applicability and timeliness, and you shall bear the risks and
        responsibilities of the consequences of use; for any loss or damage arising from your use of this service,
        including but not limited to direct loss, indirect loss, loss of profits, loss of goodwill, loss of data or
        other economic losses, even if we have been advised in advance of the possibility of such loss or damage; we
        reserve the right to amend this statement from time to time, so please check this statement regularly before
        using the Service. If you have any questions or concerns about this Statement or the Service, please contact us.
    </p>
</blockquote>

<h2> Overview </h2>

<p>ChatGPT-on-WeChat help you deploy your WeChat ChatGPT chat robot in the cloud in two steps!
    GitHub address of this project: https://github.com/kx-Huang/ChatGPT-on-WeChat</p>

<h2> Prerequisites </h2>

<p><font style="color:rgb(51, 51, 51);"> To deploy a ChatGPT-on-WeChat community edition service instance, you need to
    access and create some Alibaba Cloud resources. Therefore, your account must contain permissions for the following
    resources. </font><font style="color:rgb(51, 51, 51);"> </font><strong><font style="color:rgb(51, 51, 51);">
    Description </font></strong><font style="color:rgb(51, 51>: 51);">: this permission is required only when your account is a RAM account. </font></p>

<table>
<thead>
<tr>
<th><font style = " color:rgb(51, 51, 51);"> Permission policy name </font></th>
    <th><font style="color:rgb(51, 51, 51);"> Remarks </font></th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><font style="color:rgb(51, 51, 51);">AliyunECSFullAccess</font></td>
        <td><font style="color:rgb(51, 51, 51);"> Permissions to manage ECS </font></td>
    </tr>
    <tr>
        <td><font style="color:rgb(51, 51, 51);">AliyunVPCFullAccess</font></td>
        <td><font style="color:rgb(51, 51, 51);"> Permissions to manage a VPC </font></td>
    </tr>
    <tr>
        <td><font style="color:rgb(51, 51, 51);">AliyunROSFullAccess</font></td>
        <td><font style="color:rgb(51, 51, 51);"> Manage permissions for the Resource Orchestration Service
            (ROS) </font></td>
    </tr>
    <tr>
        <td><font style="color:rgb(51, 51, 51);">AliyunComputeNestUserFullAccess</font></td>
        <td><font style="color:rgb(51, 51, 51);"> Manage user-side permissions for the compute nest service
            (ComputeNest) </font></td>
    </tr>
    </tbody>
    </table>

<h2> Billing instructions </h2>

<p><font style="color:rgb(51, 51, 51);"> The cost of ChatGPT-on-WeChat community edition deployment in computing nest
    mainly involves:</font></p>

<ul>
    <li><font style="color:rgb(51, 51, 51);"> selected vCPU and memory specifications </font></li>
    <li><font style="color:rgb(51, 51, 51);"> System disk type and capacity </font></li>
    <li><font style="color:rgb(51, 51, 51);"> Internet bandwidth </font></li>
</ul>

<p> This service requires a WeChat server that can access the public network from the ECS instance. </p>

<h2> Deployment Architecture </h2>

<p> This service is deployed on a single ECS instance. The architecture is as follows:</p>

<p><img src="./images/architecture_ecs_single.png" alt=""/></p>

<h2> Parameter description </h2>

<table>
    <thead>
    <tr>
        <th><font style="color:rgb(51, 51, 51);"> parameter group </font></th>
        <th><font style="color:rgb(51, 51, 51);"> parameter items </font></th>
        <th><font style="color:rgb(51, 51, 51);"> Description </font></th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><font style="color:rgb(51, 51, 51);"> Service instance </font></td>
        <td><font style="color:rgb(51, 51, 51);"> Service instance name </font></td>
        <td><font style="color:rgb(51, 51, 51);"> No more than 64 characters in length, must start with an English
            letter, and can contain numbers, English letters, dashes (-), and underscores (_)</font></td>
    </tr>
    <tr>
        <td></td>
        <td><font style="color:rgb(51, 51, 51);"> Region </font></td>
        <td><font style="color:rgb(51, 51, 51);"> Region where the service instance is deployed </font></td>
    </tr>
    <tr>
        <td></td>
        <td><font style="color:rgb(51, 51, 51);"> Payment type </font></td>
        <td><font style="color:rgb(51, 51, 51);"> Resource billing type: Pay-As-You-Go and Subscription </font></td>
    </tr>
    <tr>
        <td><font style="color:rgb(51, 51, 51);"> resource configuration </font></td>
        <td><font style="color:rgb(51, 51, 51);"> instance type </font></td>
        <td><font style="color:rgb(51, 51, 51);"> Instance specifications available in the Availability Zone </font>
        </td>
    </tr>
    <tr>
        <td></td>
        <td><font style="color:rgb(51, 51, 51);"> Instance password </font></td>
        <td><font style="color:rgb(51, 51, 51);"> is 8-30 in length and must contain three items (uppercase letters,
            lowercase letters, numbers, ()'~! @#$%^& *-+ ={}[]:;,.? Special symbols in)</font></td>
    </tr>
    <tr>
        <td><font style="color:rgb(51, 51, 51);"> Availability Zone Configuration </font></td>
        <td><font style="color:rgb(51, 51, 51);"> Availability Zone </font></td>
        <td><font style="color:rgb(51, 51, 51);"> Zone where the ECS instance is located </font></td>
    </tr>
    <tr>
        <td></td>
        <td><font style="color:rgb(51, 51, 51);">VPC ID</font></td>
        <td><font style="color:rgb(51, 51, 51);"> VPC where the resource is located </font></td>
    </tr>
    <tr>
        <td></td>
        <td><font style="color:rgb(51, 51, 51);"> Switch ID</font></td>
        <td><font style="color:rgb(51, 51, 51);"> Switch where the resource is located </font></td>
    </tr>
    <tr>
        <td><font style="color:rgb(51, 51, 51);"> Software Configuration </font></td>
        <td><font style="color:rgb(51, 51, 51);">OpenAI Api key</font></td>
        <td><font style="color:rgb(51, 51, 51);"> Api key for OpenAI, required </font></td>
    </tr>
    <tr>
        <td></td>
        <td><font style="color:rgb(51, 51, 51);">OpenAI Organization ID</font></td>
        <td><font style="color:rgb(51, 51, 51);">OpenAI Organization ID, optional </font></td>
    </tr>
    <tr>
        <td></td>
        <td><font style="color:rgb(51, 51, 51);">ChatGPT trigger keyword </font></td>
        <td><font style="color:rgb(51, 51, 51);"> In private chat, the message begins with a keyword will trigger an
            automatic reply. In group chat, the message begins with @ robot
            <keyword> will trigger an automatic reply. The keyword can be an empty string, that is, each message in the
                private chat will trigger an automatic reply, and only "@ robot" in the group chat will trigger an
                automatic reply
        </font></td>
    </tr>
    </tbody>
</table>

<h2> Deployment process </h2>

<ol>
    <li> visit the compute nest ChatGPT-on-WeChat<a
            href="https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-a81e49ab7dd24520a365">
        deployment link </a> and fill in the deployment parameters as prompted
    </li>
    <li> Select payment type
        <img src="./images/pay_type_config.png" alt=""/></li>
    <li> enter instance parameters
        <img src="./images/resource_config.png" alt=""/></li>
    <li> Fill in the zone and network parameters and click Next: Confirm Order <img src="./images/zone_config.png"
                                                                                    alt=""/></li>
    <li> Click Create Now and wait for the service instance deployment to complete</li>
    <li> After the service instance is deployed, click the instance ID to go to the details page. <img src="" alt=""/>
    </li>
    <li> Log on to the ECS instance according to the instructions in <img src="./images/QR_code.png" alt=""/></li>
    <li> Scan the latest QR code output in the application log and confirm to log in to WeChat desktop</li>
    <li> wait a few seconds to chat with wechat robot</li>
</ol>
