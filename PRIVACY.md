# Blocklist Exporter for X BETA — Privacy Policy / 隐私政策

Applies to version 1.3.0 (BETA). Updated: 2026-11-13.

Contact / 联系方式: Chrome Web Store listing support channel / Chrome 应用商店详情页的支持渠道

## English

Blocklist Exporter for X BETA helps you create local JSON files of X usernames and exact numeric account IDs. You can read the blocked-account list of the X account signed in to your current Chrome profile, or resolve a list of usernames you provide. Version 1.3.0 supports English, Simplified Chinese and Japanese, with an Auto setting that follows the browser language. It does not publish or subscribe to a remote account list.

### Information handled

The extension handles the signed-in X account's username and numeric ID, requested usernames or profile links, target account usernames and numeric IDs returned by X, and task information such as paging cursors, progress, local status messages, request deadlines and rate-limit cooldowns. The current account ID is retained with a scan so that another account cannot accidentally resume and mix into that scan.

The extension reads the `twid` account identifier and `ct0` CSRF cookie from x.com. It uses Chrome's existing X authentication session for HTTPS read requests; Chrome attaches its normal authentication cookies. The extension does not directly read `auth_token`, ask you to enter a password, or require an X API key. Cookie values remain in background memory and may be cached between requests until that worker ends or its session cache is cleared. They are not written to persistent extension storage or included in downloads.

X API replies can contain additional account fields, but the extractor retains only the identifiers and paging information needed for the chosen export. The extension has no feature to read post bodies, media, private messages or full web pages. It does not use content scripts, enumerate browser tabs, access browser history, log general keystrokes or mouse activity, or monitor visits to other websites.

### Purpose and network destinations

Data is used only for the requested account-list export: verifying the current account, obtaining accurate identifiers, following pagination, preserving progress and cooldowns, and producing your selected local file. Tasks start when you explicitly start them and may continue while the popup is closed.

The extension sends authenticated read requests only to x.com. A username lookup necessarily sends the selected username to X; blocked-list requests include the service's paging cursor. X receives the normal connection information, including the outgoing IP address, and handles requests under its own terms and privacy policy. This tool is not an anonymity service and does not hide your IP address from X.

There is no extension-operated analytics, advertising, cross-site tracking or developer upload service. The extension does not connect to GitHub, upload your list to a repository, send exports to the developer, or execute a block, unblock, report, post or other X write operation. The developer does not receive the extension's locally stored account lists or session values through this extension. Separate services you voluntarily use to share a downloaded file are outside the extension's control.

### Local storage and protection limits

Persistent tasks, results, scan-owner ID and paging progress are stored as AES-GCM-256 ciphertext in the extension's IndexedDB, using a new random IV for each saved revision. A non-extractable Web Crypto key is stored in the same database. The key and ciphertext remain in the same browser profile: this is application-level encryption, not an independent operating-system key vault. It does not guarantee protection against local malware, compromised extension code or copying an entire browser profile.

The current account binding is held in Chrome's in-memory `storage.session`. Persistent `storage.local` contains a non-sensitive revision marker after any supported legacy-state migration succeeds. If a legacy plaintext progress record exists under this same extension ID, the extension first writes and verifies an encrypted copy before removing the legacy logical record. An unreadable existing encrypted state stops operations rather than silently replacing your data.

From version 1.3.0, the interface language preference is also saved in ordinary local extension storage (`chrome.storage.local`). This non-sensitive setting contains no account information and is stored separately, without encryption; tasks and results remain encrypted as described above. It is used only to choose interface text, is not included in downloaded lists, and is not sent to the developer. Resetting or clearing tasks does not clear this preference; it remains until you change it, remove the extension data, or uninstall the extension.

The extension does not use Chrome Sync for these account lists. While it is running, the extension must also process decrypted information in memory to provide its interface and exports.

### Downloads, retention and deletion

You choose when to download `x-blocklist.json` or `x-id-map.json`. These downloads are readable, unencrypted JSON files, not encrypted backups. They contain the selected target usernames and numeric IDs; the full-list format also includes its schema, list name and export time, and the lookup format includes unresolved statuses. They do not include your account binding, cookies, internal cursors, developer-machine paths or raw request errors.

You decide whether to keep, delete or share these files. A blocklist can reveal personal blocking preferences, so consider its contents before forwarding it. Exporting a file does not automatically publish it or include it in an official community list.

Local task data stays in the extension until you reset the blocked-list scan, clear the separate username-query tasks, remove extension data through your browser, or uninstall the extension. Reset and clear controls affect their respective task areas; they do not promise to erase the current session binding or the local encryption key. Session-only state is handled by Chrome's session-storage lifecycle. Downloaded files and backups remain until you delete them separately. Logical deletion does not guarantee physical erasure of prior database pages, device backups or copied files. The exporter does not change the blocked-account list stored by X.

### Limited Use and contact

Blocklist Exporter for X BETA's use of information received from Chrome APIs adheres to the Chrome Web Store User Data Policy, including the Limited Use requirements. Data is used only for the disclosed export features. It is not sold, used for personalized advertising, transferred for unrelated purposes, or used for creditworthiness or lending decisions. The only extension-initiated transfer described here is the interaction with X necessary to carry out the requested reads.

If you voluntarily contact support, the information you send can be used to answer your request. Do not send passwords, session cookies or API keys. Use the support channel on this extension's Chrome Web Store listing for privacy questions or help with local deletion. This policy does not imply that a beta build has passed store review or that X's internal endpoints will remain available.

## 简体中文

Blocklist Exporter for X BETA 用于把 X 用户名和精确的数字账号 ID 保存为本机 JSON。你可以读取当前 Chrome 个人资料中已登录 X 账号的屏蔽名单，也可以查询自己提供的一组用户名。1.3.0 版界面支持简体中文、日语和英语，并可选择 Auto 跟随浏览器语言。它不发布或订阅远程账号名单。

### 处理哪些信息

扩展处理当前 X 账号的用户名和数字 ID、你输入的用户名或主页链接、X 返回的目标用户名和数字 ID，以及分页游标、任务进度、本机状态文字、请求期限和限流冷却时间。读取进度会保留所属账号的数字 ID，以防续读时混入另一个账号的结果。

扩展读取 x.com 的 `twid` 账号标识和 `ct0` CSRF Cookie，借助 Chrome 中现有的 X 登录会话发送 HTTPS 只读请求。Chrome 会附带正常的认证 Cookie。扩展不直接读取 `auth_token`，不要求在扩展内输入密码，也不要求提供 X API Key。Cookie 值只留在后台内存中；可能在请求间缓存，直到后台结束或会话缓存被清除，不写入扩展持久存储或下载文件。

X API 返回的数据可能含有其他账号字段，但提取器只保留完成所选导出所需的身份和分页信息。扩展没有读取帖子正文、媒体、私信或整页网页的功能；不使用内容脚本，不枚举浏览器标签页，不访问浏览历史，不记录普通键盘或鼠标活动，也不监视其他网站的访问。

### 使用目的与联网范围

这些数据只用于你请求的账号名单导出：核对当前账号、取得准确 ID、分页、保存进度与冷却状态，以及生成你选择下载的文件。只有你主动启动任务后才开始读取；已启动的任务可以在关闭小窗口后继续。

扩展仅向 x.com 发送经过认证的读取请求。查询用户名时需要把该用户名发送给 X；读取屏蔽列表时会使用 X 返回的分页游标。X 会收到普通连接信息，包括出口 IP，并按其自身条款和隐私政策处理请求。本工具不是匿名服务，不会向 X 隐藏你的 IP。

扩展没有自建分析统计、广告、跨站追踪或开发者上传服务；不连接 GitHub，不把名单上传仓库，不把导出文件发给开发者，也不执行拉黑、取消拉黑、举报、发帖或其他 X 写入操作。开发者不会通过本扩展收到你本机保存的账号名单或会话值。你自愿选择其他服务分享下载文件时，这些外部服务不在扩展控制范围内。

### 本机存储与保护边界

持久任务、结果、进度所属账号 ID 和分页信息，以 AES-GCM-256 密文保存于扩展的 IndexedDB，每次写入新版本时使用新的随机 IV。不可通过 Web Crypto 普通导出方法导出的密钥也保存在同一个数据库中。密钥与密文仍位于同一浏览器个人资料内，这是应用层加密，不是独立的操作系统密钥保险箱；不能保证抵御本机恶意程序、扩展代码被攻破或整个浏览器资料被复制。

当前账号绑定保存在 Chrome 的内存 `storage.session` 中。受支持的旧状态迁移成功后，持久 `storage.local` 保留不含账号信息的版本通知标记。如果同一扩展 ID 下已有旧的明文任务记录，会先写入并验证加密副本，再删除旧的逻辑记录。已有加密数据无法读取时，工具会停止操作，不会悄悄用空数据替换。

从 1.3.0 版起，界面语言偏好也保存在普通本机扩展存储（`chrome.storage.local`）中。这项非敏感设置不含账号信息，单独以未加密形式保存；任务和结果仍按上述方式加密。它只用于选择界面文字，不会写入下载名单，也不会发送给开发者。重置或清空任务不会清除语言偏好；它会保留到你更改设置、移除扩展数据或卸载扩展。

扩展不使用 Chrome Sync 同步这些名单。运行时，为了显示界面和生成导出文件，也需要在内存中处理解密后的数据。

### 下载、保留与删除

由你决定何时下载 `x-blocklist.json` 或 `x-id-map.json`。这些文件是可直接阅读、没有加密的 JSON，不是加密备份。文件包含所选目标的用户名和数字 ID；完整名单格式还包含 schema、名单名称和导出时间，用户名查询格式还包含未解决状态。它们不包含当前账号绑定、Cookie、内部游标、开发机路径或原始请求错误。

是否保留、删除或分享文件由你决定。屏蔽名单可能反映个人屏蔽偏好，转发前请考虑其中内容。导出不会自动发布名单，也不会自动加入官方社区名单。

本机任务数据会保留到你重置屏蔽名单进度、清空独立的用户名查询任务、通过浏览器移除扩展数据或卸载扩展。重置和清空按钮只作用于各自任务区，不承诺删除当前会话绑定或本机加密密钥。内存会话数据遵循 Chrome 的会话存储生命周期。下载文件及备份需另行删除。逻辑删除不保证物理擦除历史数据库页、设备备份或已复制文件。导出器不会改变 X 服务上保存的屏蔽列表。

### 有限使用与联系

Blocklist Exporter for X BETA 对从 Chrome API 获得的信息的使用遵守 Chrome Web Store 用户数据政策，包括 Limited Use 要求。数据仅用于披露的导出功能，不出售、不用于个性化广告、不为无关目的转移，也不用于信用评估或贷款决策。本政策描述的扩展主动传输，仅限完成所请求读取所需的 X 交互。

如果你自愿联系支持渠道，提供的信息可用于答复你的问题。请勿发送密码、会话 Cookie 或 API Key。隐私疑问或本机数据删除问题，请通过本扩展 Chrome 应用商店详情页的支持渠道联系。本政策不表示 BETA 已通过商店审核，也不保证 X 网页内部接口持续可用。
