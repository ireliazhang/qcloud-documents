在 CNAME 接入方式下，用户无需将 DNS 解析权转移给 EdgeOne，只需添加记录（子域名）并开启代理，在 DNS 解析商处添加指定的 CNAME 记录，即可接入 EdgeOne 安全/加速服务。
 

## 添加记录（子域名接入）[](id:add)
在CNAME 接入方式下，通过添加记录来为该站点的子域名接入相应的服务。

1. 登录 [边缘安全加速平台控制台](https://console.cloud.tencent.com/edgeone)，在左侧菜单栏中，单击**域名服务**。
2. 在域名服务页面，选择所需站点，单击**添加域名**。
![image](https://user-images.githubusercontent.com/115441986/198982372-96a48000-93a6-4b9c-b7e9-da864a9a488b.png)
3. 填写相关参数，单击**保存**。
![image](https://user-images.githubusercontent.com/115441986/198982460-71372abc-5513-48e3-9d81-0ef1b4e8a3a2.png)

**参数说明：**
 - 加速域名：填写需开启加速的子域名，仅需输入子域名的前缀。
 - 源站类型：可选择 IPv4/IPv6/域名。
 - 源站地址：源站类型和源站地址示例如下
<table>
<thead>
<tr>
<th>源站类型</th>
<th>源站地址示例</th>
<th>用途说明</th>
</tr>
</thead>
<tbody><tr>
<td>IPv4</td>
<td>8.8.8.8</td>
<td>回源到一个 IPv4 源站，源站地址为 8.8.8.8</td>
</tr>
<tr>
<td>IPv6</td>
<td>2400:cb00:2049:1::a29f:f9</td>
<td>回源到一个 IPv6 源站，源站地址为 2400:cb00:2049:1::a29f:f9。<br>EdgeOne 默认支持双栈回源</td>
</tr>
<tr>
<td>域名</td>
<td>www.origin.com</td>
<td>回源到一个域名源站，源站地址为 www.origin.com</td>
</tr>
</tbody></table>
 - 代理模式：支持开启/关闭代理，更多详情请参见 [代理模式](https://cloud.tencent.com/document/product/1552/70786)。
 - CNAME：开启代理后系统自动生成，用户需在 DNS 服务商处添加该 CNAME 记录。
 - HTTPS 证书：在 CNAME 接入方式下，系统不提供 EdgeOne 通用证书。需要手动为每个子域名关联证书，方可正常使用 HTTPS 服务。

4. 保存记录之后，EdgeOne会给您的子域名分配一个 CNAME，您还需要前往您的 DNS 解析服务商完成 CNAME 配置，才可以将用户的访问指向 EdgeOne 节点，使加速生效
以下为腾讯云 DNSPod 控制台的配置方法：
(1)复制当前域名的 CNAME 值
![image](https://user-images.githubusercontent.com/115441986/199001721-6c326fc8-1556-4683-9a4f-422c6d8439b1.png)
(2)前往 DNS 解析 DNSPod 控制台，找到对应的域名，单击解析按钮
![image](https://user-images.githubusercontent.com/115441986/199006381-b5d914ef-2b2f-4972-a4d6-b7c99403789a.png)
(3)点击添加记录。主机记录按照提示填写即可，记录类型选择 CNAME ，记录值填写第一步中复制的 CNAME，其他参数维持不变。
![image](https://user-images.githubusercontent.com/115441986/199006620-fe3a9c40-812e-4442-9991-44565afeed24.png)
(4)单击保存后，即可完成 CNAME 配置。

5. 配置完成之后，域名服务列表中，CNAME 列出现绿色的 icon 则表示该 CNAME 记录已生效，该子域名正常加速中。
![image](https://user-images.githubusercontent.com/115441986/199007807-b6c94562-53bb-42c8-ac2e-005f8bf1b71c.png)



