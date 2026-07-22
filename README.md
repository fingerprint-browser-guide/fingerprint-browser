# 2026 指纹浏览器评测与选择指南

本项目基于公开来源，持续核查主流**指纹浏览器、反检测浏览器和防关联浏览器**的功能、价格、版本变化与适用场景。项目区分官方资料、公开核查、编辑分析与实际测试；尚未完成验证的信息不会作为确定结论或产品排名。

> 当前状态：首轮公开资料核查与证据库建设完成。已覆盖 6 个平台，最后核查日期为 **2026-07-17**。首版没有统一条件下的真实横向测试，因此不提供成功率、100 分制或“最佳指纹浏览器”总榜。

## 先给结论：指纹浏览器应该怎么选

不要先看总分，先按不可妥协的约束筛选：

1. 客户端是否支持你的 Windows、macOS、Linux 或 Android 设备；
2. 是否需要 Chromium、Firefox 或两种内核；
3. 环境数据默认保存在本地、云端，还是可以切换；
4. 是否支持你的代理协议、API 和自动化框架；
5. 团队成员、权限、环境分享和操作记录是否够用；
6. 用真实环境数和成员数比较总成本，而不是只看广告起价。

代理只处理网络路径，不能自动隔离 Cookie 或协调浏览器指纹；无痕模式主要减少本机浏览记录，也不会自动建立新的稳定环境。基础概念见[什么是指纹浏览器](docs/what-is-a-fingerprint-browser.md)。

## 六个平台快速对比

以下按产品英文名排序，不代表名次。

| 产品 | 客户端系统 | 内核 | 免费额度 | 自动化 | 公开的数据存储口径 |
|---|---|---|---:|---|---|
| [AdsPower](https://www.adspower.com) | Windows、macOS、Ubuntu | Chromium、Firefox | 2 个环境 | Local API、RPA | 本地缓存；可选云同步 |
| [Dolphin Anty](https://dolphin-anty.com) | Windows、macOS、Linux | Chromium | 5 个环境 | API、CDP、Selenium、Puppeteer、Playwright | 本地；可选云同步 |
| [GoLogin](https://gologin.com) | Windows、macOS、Linux、Android | Orbita（Chromium） | 3 个环境 | REST API、Selenium、Puppeteer、Playwright | 云同步；运行时有本地临时数据 |
| [MoreLogin](https://www.morelogin.com) | Windows、macOS | Chrome、Firefox | 2 个环境、2 个成员 | Local API、Selenium、Puppeteer | 本地缓存；可选云同步 |
| [Multilogin](https://multilogin.com) | Windows、macOS、Ubuntu | Chromium 系；Firefox 系（legacy） | 5 个环境 | API、Selenium、Puppeteer、Playwright | 云端或本地；移动环境仅云端 |
| [Web4 Browser](https://web4browser.io) | Windows、macOS | Fingerprint Chromium、Fingerprint Firefox | 3 个环境 | CDP、Headless、Selenium、Puppeteer、Playwright、MCP | 浏览器数据默认本地存储 |

完整操作系统版本、团队功能、代理、来源 URL 和限制见[产品事实 CSV](data/products.csv)与[六个平台详细对比](docs/comparison.md)。“官方资料列出支持”不等于本项目已验证其稳定性，也不表示免费套餐一定包含。

## 目前最值得注意的公开资料问题

- **动态价格**：AdsPower 的公开价格页列出套餐和环境档位，但金额由动态选择器生成，本次页面没有稳定返回静态起价，因此没有从第三方文章补数。
- **页面内部矛盾**：GoLogin 价格帮助页的计划表写 Professional 年付月均 4.5 美元起，同页 FAQ 示例却重复写为 9 美元。对应年付记录标为 `unverified`。
- **内核口径**：Dolphin Anty 设置文档明确写基于 Chromium；其价格页抓取文本同时出现“Chrome or Firefox engine”，因此本项目不把 Firefox 支持写成确定事实。
- **概念混用**：环境可以模拟 Android/iOS 参数，不等于客户端可以安装在手机系统上。本项目将两类字段分开。
- **旧内核路线**：Multilogin 当前帮助页将 Stealthfox 标为 legacy，并说明不再获得内核更新；需要 Firefox 风格环境时应先确认这一限制。

这些冲突和缺失是证据库的一部分，不会为了填满表格而隐藏。

## 如何阅读证据标签

| 标签 | CSV 值 | 含义 |
|---|---|---|
| 官方资料 | `official` | 一个官方公开页面直接支持 |
| 公开核查 | `cross_checked` | 至少两个公开来源相互支持，或不同官方页面交叉确认 |
| 编辑分析 | `editorial_analysis` | 基于列明证据作出的解释，不是实测结果 |
| 实际测试 | `tested` | 已公开环境、版本、步骤、日期、截图或日志 |
| 待核实 | `unverified` | 来源不足、页面冲突或暂时无法确认 |

首版数据没有 `tested` 记录。厂商演示、一次成功、没有原始证据的“独立测试”都不满足该标签要求。完整规则见[评估方法](METHODOLOGY.md)。

## 仓库内容

| 文件 | 用途 |
|---|---|
| [产品事实](data/products.csv) | 操作系统、内核、自动化、团队、代理、存储和免费额度的机器可读记录 |
| [价格记录](data/pricing.csv) | 带计费周期、容量、币种、来源和日期的代表性价格快照 |
| [六个平台详细对比](docs/comparison.md) | 按硬约束筛选产品的中文分析 |
| [什么是指纹浏览器](docs/what-is-a-fingerprint-browser.md) | 定义及与无痕模式、代理、VPN、虚拟机的区别 |
| [来源账本](SOURCES.md) | 每个结论对应的官方页面、用途、状态和核查日期 |
| [评估方法](METHODOLOGY.md) | 纳入标准、证据等级、价格标准化和冲突处理 |
| [更新记录](CHANGELOG.md) | 产品、字段、价格、来源和结论的变更历史 |
| [免责声明](DISCLAIMER.md) | 时效性、厂商声明边界、商业链接与合法使用范围 |

## 当前能回答与不能回答的问题

本项目目前可以回答：各平台官方公开支持哪些客户端系统和内核；是否公开 API、团队、代理与存储能力；免费额度和代表性公开价格是什么；哪些页面存在冲突或缺失。

本项目目前不能回答：哪个平台风控通过率最高、长期账号存活率、统一代理下的检测表现、大规模并发稳定性、客服与退款执行情况。回答这些问题需要统一环境、可复查步骤和原始证据。

## 产品范围与中立处理

首版覆盖 AdsPower、Dolphin Anty、GoLogin、MoreLogin、Multilogin 和 Web4 Browser。六个平台使用相同字段、来源优先级和证据标签，不设置额外权重、默认推荐或特殊评分。资料多不等于产品更好，资料少也不会用猜测补全。

项目不宣称自己是独立第三方认证机构。首版所有产品链接均用于指向来源，没有联盟参数；未来若出现推广链接、赞助、付费排名或其他可能影响判断的商业内容，应在相关页面清晰标注。

## 使用边界

本项目面向合法的隐私保护、网站兼容性测试、广告验证、跨境业务、授权账号管理、环境研究和浏览器自动化。它不提供批量虚假注册、身份验证规避、账号交易、欺诈、撞库、风控绕过或其他滥用指导。

任何指纹浏览器都不能保证目标网站接受环境，也不能替代平台条款、账号安全和合规审查。详见[免责声明](DISCLAIMER.md)。

## 纠错与更新

发现价格变化、失效链接或事实错误时，欢迎提交 issue。请尽量附上产品、字段、当前记录、官方 URL、访问日期和建议修改内容。无法公开核查的内部说法不会直接覆盖现有证据。

本次重构变化见[更新记录](CHANGELOG.md)。
