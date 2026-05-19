# 隐私声明 · Privacy Policy

**生效日期 · Effective Date**: 2026-05-15
**适用产品 · Applies To**: AI 配置校验助手
**版本 · Version**: 1.0.0
**联系邮箱 · Contact**: config.validation@gmail.com

---

## 一、概述 · Overview


「AI 配置校验助手」（以下简称"本插件"）是一款仅服务于公司内部配置平台的 Chrome 浏览器扩展。本插件在用户发布配置时自动触发 AI 校验，识别配置变更中的潜在风险并展示校验结果。本声明说明本插件在使用过程中**会**与**不会**收集哪些数据、如何使用以及如何保护这些数据。


The "AI Config Validator" (hereinafter "the Extension") is a Chrome browser extension exclusively designed for use with the company's internal configuration platforms. When a user publishes settings on a supported platform, the Extension automatically triggers an AI validation flow, identifies potential risks in the configuration change, and presents the result. This Policy explains what data the Extension **does** and **does NOT** collect, how it is used, and how it is protected.

---

## 二、单一目的声明 · Single Purpose Statement


本插件的**单一目的**是：在用户提交配置发布请求时，自动调用 AI 校验服务进行风险扫描，对未通过校验的高风险变更进行拦截或要求用户确认风险后才能放行。本插件**不会**用于任何与该单一目的无关的用途。


The **single purpose** of the Extension is: when a user submits a configuration release request, automatically invoke the AI validation service to scan for risks, and either block the high-risk change or require explicit risk confirmation before allowing it to proceed. The Extension is **NOT** used for any purpose unrelated to this single purpose.

---

## 三、数据收集与使用 · Data Collection & Usage

### 3.1 我们不收集的数据 · Data We Do NOT Collect

本插件**不会**收集以下任何类型的数据 / The Extension does **NOT** collect any of the following:

- ❌ 个人身份信息（PII）/ Personally Identifiable Information (PII)
- ❌ 健康信息 / Health information
- ❌ 财务及支付信息 / Financial or payment information
- ❌ 身份验证凭据（密码、Cookie、Token 等）/ Authentication credentials (passwords, cookies, tokens)
- ❌ 个人通信内容（邮件、聊天记录等）/ Personal communications (emails, chat logs)
- ❌ 地理位置信息 / Geolocation data
- ❌ 设备唯一标识符（IMEI、MAC 等）/ Device unique identifiers (IMEI, MAC, etc.)
- ❌ 浏览历史 / Browsing history
- ❌ 任何与"配置校验"无关的页面内容 / Any page content unrelated to configuration validation

### 3.2 我们收集的数据 · Data We DO Collect

| 数据类型<br/>Data Type | 触发场景<br/>Trigger | 用途<br/>Purpose |
|---------|---------|------|---------|
| **待校验配置数据**<br/>Configuration to validate | 用户在受支持平台发布配置<br/>User clicks "Publish" on a supported platform | 调用 AI 校验接口对配置进行风险扫描<br/>Invoke the AI validation API to scan for risks | 
| **用户操作埋点**<br/>User-action tracking | 校验成功 / 强制发布 / 取消发布<br/>Validation success / forced publish / cancellation | 内部统计分析<br/>Internal analytics| 

---

## 四、数据存储与保留 · Data Storage & Retention


- 本插件**不会**在本地（浏览器 storage、localStorage、IndexedDB 等）持久化保存任何用户数据
- 校验数据仅在用户点击发布的瞬间临时通过 HTTPS 传输至内部 AI 校验服务
- 校验完成后，数据由 AI 校验后端按公司内部数据保留策略管理，本插件不再持有副本
- 用户可通过浏览器扩展管理页面（`chrome://extensions`）随时**禁用或卸载**本插件，立即停止任何数据采集与上报


- The Extension does **NOT** persist any user data locally (no browser storage, localStorage, IndexedDB, etc.)
- Validation data is only transmitted via HTTPS to the company's internal AI validation service at the moment the user clicks "Publish"
- After validation completes, the data is managed by the AI validation backend per the company's internal data-retention policy. The Extension does NOT keep any copy
- Users can **disable or uninstall** the Extension at any time via `chrome://extensions`, which immediately stops all data collection and reporting

---

## 五、数据共享 · Data Sharing


- 本插件**不会**将任何数据出售、交易或转让给任何第三方
- 本插件**不会**将数据用于广告、用户画像、信用评估或借贷等目的
- 所有数据仅在公司内网传输与处理
- 不存在任何第三方分析 SDK、广告 SDK 或外部追踪器


- The Extension does **NOT** sell, trade, or transfer any data to any third party
- The Extension does **NOT** use data for advertising, user profiling, credit scoring, or lending purposes
- All data is transmitted and processed exclusively within the company's internal network
- There are NO third-party analytics SDKs, advertising SDKs, or external trackers

---

## 六、权限说明 · Permission Disclosure

### 6.1 Host Permissions

用于从 Background Service Worker 向公司内部 AI 校验服务发起跨域请求。完整的 host 权限范围请参阅本插件 manifest.json 中的 `host_permissions` 字段。

Used by the Background Service Worker to send cross-origin requests to the company's internal AI validation service. Refer to the `host_permissions` field in the Extension's manifest.json for the exact host scope.

### 6.2 Content Scripts (限定域名白名单 / Domain Allowlist)

拦截器脚本必须运行在 MAIN World 才能 Hook 页面级 `fetch` / `XMLHttpRequest`。本插件已将 content script 的 `matches` 严格限定为收录在内部白名单（`MATCH_PATTERNS`）中的少量公司内部配置平台域名，**未采用 `<all_urls>` 或任何宽泛匹配**。在白名单外的任何网站上，本插件**不会**被浏览器加载，零干扰、零数据采集。运行时还会通过与业务规则联动的 host 二次校验，只有命中预置内部平台规则的请求才会触发校验流程。完整的匹配范围请参阅本插件 manifest.json 中的 `content_scripts.matches` 字段。

The interceptor script must run in the MAIN World to hook the page-level `fetch` / `XMLHttpRequest`. The Extension strictly limits each content script's `matches` to a small allowlist (`MATCH_PATTERNS`) of internal corporate configuration-platform domains — **`<all_urls>` and other broad patterns are NOT used**. On any website outside the allowlist, the Extension is **NOT** loaded by the browser, resulting in zero interception and zero data collection. At runtime, an additional host check tied to the business rules ensures that the validation flow is triggered ONLY when a pre-configured internal platform rule matches. Refer to the `content_scripts.matches` field in the Extension's manifest.json for the exact match scope.

---

## 七、用户权利 · User Rights


用户有权：

- **知情权**：通过本声明了解本插件的数据处理方式
- **拒绝权**：通过卸载本插件停止任何数据收集
- **访问权**：联系内部研发负责人，查询自己的埋点数据记录
- **删除权**：联系内部研发负责人，请求删除自己的埋点数据记录


Users have the right to:

- **Be Informed**: Understand the Extension's data-handling practices through this Policy
- **Opt-out**: Stop all data collection by uninstalling the Extension
- **Access**: Contact the internal maintainer to query their tracking records
- **Erasure**: Contact the internal maintainer to request deletion of their tracking records

---

## 八、数据安全 · Data Security


- 所有数据传输均使用 HTTPS 加密通道
- 本插件不引用任何远程托管的 JavaScript 代码（符合 Chrome Web Store Manifest V3 政策）
- 校验数据通过 Background Service Worker 代理转发，避免 MAIN World 直接访问敏感接口
- UI 通过 Shadow DOM 隔离渲染，与宿主页面 CSS、DOM 完全隔离，避免被宿主页面脚本读取


- All data transmissions use HTTPS-encrypted channels
- The Extension does NOT reference any remotely hosted JavaScript (compliant with Chrome Web Store Manifest V3 policy)
- Validation data is proxied through the Background Service Worker, preventing the MAIN World from directly accessing sensitive endpoints
- The UI is rendered inside a Shadow DOM, fully isolated from the host page's CSS and DOM, preventing host-page scripts from reading it

---

## 九、未成年人保护 · Children's Privacy


本插件仅供公司内部员工在工作场景下使用，不面向未成年人提供服务，不收集未成年人的任何个人信息。


The Extension is intended exclusively for the company employees in work scenarios. It is NOT directed at minors and does NOT collect any personal information from minors.

---

## 十、政策变更 · Policy Changes


本声明可能因功能迭代、合规要求或法律法规调整而更新。重大变更时，我们会在本插件的版本说明（changelog）中明确告知，并更新本文档顶部的"生效日期"。继续使用本插件即视为接受更新后的隐私声明。


This Policy may be updated due to feature iterations, compliance requirements, or changes in laws and regulations. For significant changes, we will explicitly note them in the Extension's changelog and update the "Effective Date" at the top of this document. Continued use of the Extension constitutes acceptance of the updated Privacy Policy.

---

## 十一、联系我们 · Contact Us


如对本隐私声明有任何疑问、投诉、建议或希望行使本声明第七条所列权利，请联系本插件的研发负责人.


If you have any questions, complaints, or suggestions regarding this Privacy Policy, or if you wish to exercise the rights listed in Section 7, please contact the Extension's internal maintainer.

---

> **重要提示 · Important Note**
>
> 本插件仅服务于公司内部网络环境。在公司外部网络或任何非公司内部域名下，本插件**不会**激活任何拦截、网络请求或数据采集行为。
>
>  The Extension is exclusively designed for the company internal network. When operating outside the company network or on any non-internal domain, the Extension does **NOT** activate any interception, network request, or data-collection behavior.
