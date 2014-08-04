 xiaoyanit.github.io 
-----------------

##### My github blog ..... #####

FireFox性能相关参数


	
	//user_pref(key,value)等同于从about:config修改,删除之后,修改的设置仍然有效.
	//pref(key,value) 会覆盖默认设置,在删除之后会恢复默认设置.
	
	
	//链接-------------------------------------------------------------
	user_pref("network.http.pipelining", true);  //开启http链接？默认false
	user_pref("network.http.pipelining.ssl", true);  //开启 ssl链接？默认false
	user_pref("network.http.proxy.pipelining", true);  //开启代{过}{滤}理链接？默认false
	
	user_pref("network.http.max-connections", 48);  //默认256，Opera默认64，FF可同时打开最大HTTP连接数(1~65535)，该值是不能被突破的，
	//256肯定大了，一般的配置跑到40几条连接数就卡死了，限制该值是最彻底降低CPU消耗的办法之一
	//但是该值太小，确实就很快就满了，满了之后新的链接就得等着了
	
	user_pref("network.http.pipelining.maxrequests", 32);  //默认32，链接中最大请求数，上限65535
	user_pref("network.http.pipelining.max-optimistic-requests" , 2);//默认4，当可以发送链接时，一次发送几个链接？该参数是新加入的
	user_pref("network.http.max-persistent-connections-per-proxy", 4);  //默认32, http单个代{过}{滤}理最大连接数 参考  使用GAE代{过}{滤}理，一个app就是1个线程
	
	user_pref("network.http.keep-alive.timeout", 30);  //默认115秒，持续链接时间？秒, KB上说超过115秒不好，但没说小于115不好，我决定让持续链接加速断开
	user_pref("network.http.request.max-start-delay", 0);  //默认10秒，持续链接超越最大上限前等待时间？秒；既然可以突破上限，为啥还等待啊？？？
	//当2个persistent-connections用完时, 又要发起新的连接，实际上可以突破上限创建新的persistent-connections，但总数不能超过服务器或浏览器链接上限
	
	//其他网络相关-------------------------------------------------------------
	user_pref("network.http.redirection-limit", 5);//最大重定向次数？默认20次，只身对HTTP重定向，不包括HTML 的meta标签记忆JavaScript的，该参数用来防止重定向死循环
	user_pref("network.dns.disableIPv6",true);//关闭 ipv6 的dns解析？
	user_pref("network.dnsCacheExpiration",7200);//缓存过期时间？秒，默认900秒  
	user_pref("network.dns.disablePrefetch",false);//关闭dns预解析？
	user_pref("network.dns.disablePrefetchFromHTTPS",true);//关闭HTTPS网站的DNS预解析？默认不存在
	
	//JavaScript-------------------------------------------------------------
	user_pref("javascript.options.xml.content", true);  //开启E4X语言支持？默认false，E4X：出色的 JavaScript 。另外，可为新版火狐解决UC脚本兼容问题
	user_pref("javascript.options.xml.chrome", true); //同上
	user_pref("jsloader.reuseGlobal", true); //全局重用JS脚本？如果设为true，可以减少内存占用，但是可能造成脚本的干扰；默认false
	
	//弹窗-------------------------------------------------------------
	user_pref("dom.disable_open_during_load", true);  //禁止页面载入时弹窗？那必须的！
	user_pref("privacy.popups.policy", 2); //弹窗策略？1 允许弹窗；2 禁止弹窗；
	user_pref("dom.popup_maximum", 2); //同时弹出的窗口数？默认20，即使当popup blocker被禁用时也有效
	user_pref("privacy.popups.showBrowserMessage",true);//显示PB拦截到弹窗的消息栏？默认true显示，
	
	//JavaScript弹窗-------------------------------------------------------------
	user_pref("dom.disable_window_open_feature.close", true); //禁止隐藏关闭按钮？
	user_pref("dom.disable_window_open_feature.location", true);  //禁止隐藏地址栏？
	user_pref("dom.disable_window_open_feature.directories",true);//禁止隐藏书签栏？
	user_pref("dom.disable_window_open_feature.minimizable", true); //禁止弹窗最小化？
	user_pref("dom.disable_window_open_feature.resizable", true); //禁止重置窗口大小？
	user_pref("dom.disable_window_open_feature.scrollbars", true);  //禁止隐藏滚动条？
	user_pref("dom.disable_window_open_feature.status", true);  //禁止隐藏状态栏？
	user_pref("dom.disable_window_open_feature.titlebar", true);  //禁止隐藏标题栏？
	user_pref("dom.disable_window_open_feature.toolbar", true);  //禁止隐藏导航栏？
	user_pref("dom.disable_window_move_resize", true); //禁止JS移动和改变弹出窗口的大小？ 建议true
	user_pref("dom.disable_window_flip", true); //禁止JS前置或后者窗口？ 建议true
	user_pref("dom.disable_image_src_set", false); //禁止JS改变图片？建议false，因为有些网站使用图片动画,比如google maps
	user_pref("dom.allow_scripts_to_close_windows", true);  //允许JS脚本关闭非弹出窗口？
	user_pref("dom.popup_allowed_events", "click");  //允许哪些DOM 事件弹窗
	//即使启用了阻止弹窗，还是有一部分JS可以弹窗，该参数设置具体哪些事件可以弹窗，这个要是设置为空值，那可牛逼了！什么弹窗，都是浮云了！
	//允许弹窗的事件?默认值change click dblclick mouseup reset
	
	//插件弹窗-------------------------------------------------------------
	user_pref("privacy.popups.disable_from_plugins", 2);  //插件弹窗策略，控制由flash等插件生成的弹窗
	//为了绕过popup blocker，有些网站使用插件来弹窗，该参数控制对付这种弹窗的策略
	// 0 无限制
	// 1 现在弹窗数位dom.popup_maximum 的值
	// 2 禁止网站通过flash\java弹窗（仍可使用白名单来允许个别网站）(Default in Firefox 1.5 and above and SeaMonkey)
	// 3 完全禁止插件弹窗，妈的，逼我用3（就像cookie的那条参数network.cookie.lifetimePolicy似的，毫无疑问应该选这个）
	
	//Cookie-------------------------------------------------------------
	//user_pref("network.cookie.cookieBehavior", 3); //Cookie策略，对应如下UI
	// 0 接受所有网站cookie
	// 1 仅接受来自原始网站的cookie
	// 2 禁用cookie   推荐高手设为2，这样能使cookie的数量最少，但是你需要把常去的网站加入cookie白名单
	// 3 接受基于 cookie P3P policy 策略,菜鸟推荐使用3
	
	//P3P机制-------------------------------------------------------------
	//user_pref("network.cookie.p3plevel", 3);  //P3P策略等级，上面的参数值为3时该参数才会生效
	// P3P是基于网站特点的，不是基于网站名单的
	// 0 低-afafaaaa
	// 1 中-ffffaaaa (Default)
	// 2 高- frfradaa （比较推荐）
	// 3 自定义-使用network.cookie.p3p 的设置（强烈推荐frrrafaf）
	//user_pref("network.cookie.p3p", "frrradad"); //自定义P3P策略，该参数值由8位字符组成，字符位置代表网站类型，字符本身代表策略
	// 字符本身含义
	// flag the cookie (标记该cookie)
	// downgrade the cookie to a session cookie (关闭程序时删除cookie)
	// accept the cookie （接受cookie）
	// reject the cookie （拒绝cookie）
	// 字符位置含义
	// 1 来自无隐私策略的原始网站
	// 2 来自无隐私策略的第三方网站
	// 3 在未经许可下收集个人信息的原始网站
	// 4 在未经许可下收集个人信息的第三方网站
	// 5 仅在经许可下收集个人信息的原始网站
	// 6 仅在经许可下收集个人信息的第三方网站
	// 7 不收集个人信息的原始网站
	// 8 不收集信息的第三方网站
	
	//磁盘缓存-------------------------------------------------------------
	//user_pref("config.trim_on_minimize", false);  //最小化时压缩内存占用？该参宿不能减少内存占用，只是把内存的数据置换到磁盘中，唤醒时可能会出现慢醒现象，false吧
	
	//地址栏-------------------------------------------------------------
	user_pref("browser.urlbar.autoFill", true);  //地址栏自动补全最匹配的结果
	user_pref("browser.urlbar.delay", 0);  //"自动完成补全"的延迟时间0  
	user_pref("browser.urlbar.trimURLs", false);   //隐藏 http://前缀？隐藏有啥用啊
	user_pref("browser.identity.ssl_domain_display", 2); //当进入安全的网站时，地址栏显示？0 不显示域名；1 显示顶级域名+主域名（比如google.com）；2 显示完整域名（如www.google.com）
	user_pref("browser.urlbar.maxRichResults",20);//地址栏建议数?
	user_pref("browser.urlbar.filter.javascript",true);//地址栏筛选时，排除书签脚本，即javascript:URls
	
	// 智能地址栏-------------------------------------------------------------
	// 在 选项->隐私->地址栏   中可以设置地址栏默认筛选的条件
	user_pref("browser.urlbar.match.title", "!");  //标题
	user_pref("browser.urlbar.match.url", "@");  //URL  @表示路径，好记！
	user_pref("browser.urlbar.restrict.tag", "#"); //标签
	user_pref("browser.urlbar.restrict.typed", "$");  //输入, linux输入符$，相当于光标
	user_pref("browser.urlbar.restrict.openpage", "%"); //打开的标签页, O|O|O形似并列的标签
	user_pref("browser.urlbar.restrict.bookmark", "0");  //书签，0 和 00 不用区分中英，应分配给使用频率最高的书签和标签
	user_pref("browser.urlbar.restrict.history", "00");  //历史
	
	//搜索栏-------------------------------------------------------------
	user_pref("browser.search.openintab", true);  //新标签打开搜索框的搜索结果，默认使用Alt+Enter在新标签打开
	user_pref("browser.search.context.loadInBackground", true);//后台打开搜索结果？
	
	//效果-------------------------------------------------------------
	user_pref("general.autoScroll", false);  //自动滚动屏幕？no
	user_pref("general.smoothScroll", false);//平滑滚动？no
	user_pref("general.smoothScroll.lines", false);  //箭头平滑滚动？
	user_pref("general.smoothScroll.scrollbars", false);  //滚动条平滑滚动？
	pref("browser.tabs.animate", false);   //禁用标签动画效果
	
	//标签+窗口-------------------------------------------------------------
	//user_pref("browser.tabs.insertRelatedAfterCurrent", true);  //紧邻当前标签打开相关标签，这是模仿Chrome的风格，Pale Moon默认关闭，使用旧的火狐风格
	//user_pref("browser.link.open_external", 3);  //外部程序发送给默认浏览器的链接或，在新标签页打开？ 1 重用当前标签；2 新窗口打开；3 新标签打开
	user_pref("browser.tabs.loadDivertedInBackground", true);  //外部程序发送给默认浏览器的链接（或target="_blank"这些本应该在新窗口打开的行为）后台打开？false时不改变标签焦点//注意：Google常使用target="_new"行为，
	user_pref("browser.tabs.loadInBackground", true);  //后台打开标签？前台打开标签有时候还容易卡死（多图杀狐）
	user_pref("browser.tabs.loadBookmarksInBackground", true);  //后台标签页打开书签或历史
	//user_pref("browser.tabs.closeWindowWithLastTab", false);  //关闭最后一个标签不关闭窗口
	
	user_pref("browser.link.open_newwindow", 3);  //有些链接要求打开新窗口，该参数控制如何打开
	// 1 在当前标签/窗口打开链接，好处是标签较少
	// 2 在新窗口打开链接（Default in Firefox 1.5 and older）
	// 3 在新标签页打开链接 (Default in Firefox 2.0 and newer). 好处是单窗口模式
	user_pref("browser.link.open_newwindow.restriction", 0);  //该参数是对上面参数的微调，定义了通过JavaScript 打开的窗口与 browser.link.open_newwindow 的设置是否保持一致
	// 0 完全按参数browser.link.open_newwindow 设置打开链接; (Default in Firefox 1.0.x and SeaMonkey 1.0 to 2.1a2)  建议设为0，
	// 这样就完全按照上面参数来绝对打开链接的方式了，包括所有window.open()
	// 1 完全不按照参数browser.link.open_newwindow 设置打开链接(即参数browser.link.open_newwindow 将无效);
	// 2 若网站要求有设置窗口属性的（如size）， 则在新窗口中打开，否则按照参数browser.link.open_newwindow
	// 设置打开链接(Default in Firefox 1.5 and later) 不包括通过带参数"features"的 window.open()
	// 也就是说，一旦该参数设为0，则所有链接的打开方式都是按照上面的参数来执行
	
	//快速拨号-------------------------------------------------------------
	//user_pref("browser.newtabpage.columns", 4);  //快速拨号列数
	//user_pref("browser.newtabpage.rows", 4);  //快速拨号行数
	//user_pref("browser.newtabpage.enabled", false); //开启快速拨号？
	//user_pref("browser.newtab.preload", true);  //开启新标签页 载入？
	
	//图片-------------------------------------------------------------
	//user_pref("permissions.default.image", 3); //自动载入图片？例外网站保存在文件，该参数替代了老的参数 network.image.imageBehavior
	// 1 允许所有图片载入；
	// 2 阻止所有图片载入；
	// 3 阻止来自第三方服务器的图片, MD 这比什么广告过滤都给力～
	//user_pref("browser.enable_automatic_image_resizing", true);  //自动调整图片大小以适应窗口？ false时始终显示图片原始大小 Resize images
	
	//图片内存解码相关-------------------------------------------------------------
	//根据以下设置，可以改善打开多图网站时的卡顿现象与图片不显示现象。
	user_pref("image.cache.size", 1024000); //最大解码图片缓存？bytes，默认5242880，即5120KB，即5M
	user_pref("image.cache.timeweight", 500); // A weight, from 0-1000, to place on time when comparing to size. Size is given a weight of 1000 - timeweight.
	
	//图片内存控制-------------------------------------------------------------
	user_pref("image.mem.min_discard_timeout_ms", 5000);//多长时间后自动压缩图片数据？实际时间是介于该值及该值的二倍之间；默认10秒
	user_pref("image.mem.decode_bytes_at_a_time", 16384); // 图片解码器一次调用多大数据快？单位字节
	//user_pref("image.mem.max_decoded_image_kb", 57344);//最大已解码图片大小？KB，默认256000，即256M（我们可能暂时可能设置大于该值，但是,我先试试56M够用不^^
	
	//字体+语言+编码，-------------------------------------------------------------
	user_pref("gfx.downloadable_fonts.enabled", false);  //允许下载CSS页面内可用的字体？存在安全隐患
	user_pref("browser.blink_allowed", false);  //允许闪烁字体？
	user_pref("intl.accept_languages","zh-cn,zh,zh-hk,zh-sg,zh-tw,en-us,en,en-gb");//网页语言优先显示顺序，某些网页提供几种语言编码的版本
	
	//下载-------------------------------------------------------------
	user_pref("browser.download.dir", "F:\\迅雷下载"); //使用默认下载路径？ //设为false就会每次下载都询问下载位置
	user_pref("browser.download.folderList", 2);  //默认下载路径：0 桌面；1 “用户\我的文档\下载”目录；2 “询问下载位置”
	user_pref("browser.download.manager.scanWhenDone", false);  //下载完成后扫描文件？
	
	//调试+开发-------------------------------------------------------------
	pref("view_source.editor.path", "C:\\\\Program Files\\\\EmEditor\\\\EmEditor.exe");  //外部编辑器路径，需自定义！
	pref("dom.ipc.plugins.enabled", true);//启用外部编辑器查看源代码？
	user_pref("view_source.editor.external",false);//启用外部编辑器查看源代码？
	
	//插件假死监控器ASAP-------------------------------------------------------------
	user_pref("dom.ipc.plugins.timeoutSecs", 7); //plugin hang detector会检查插件是否停止响应了，如果已经挂了，那么会等待一段之间，然后杀掉这个死得插件，默认值45秒    Plugin hang detector
	//该值设为-1表示禁用“插件假死监控器”，但是不等于禁用了”插件容器”, 若要禁用”插件容器”需要修改dom.ipc.plugins.enabled Firefox to get Plugin Hang protection
	
	//Misc-------------------------------------------------------------
	user_pref("plugins.click_to_play", true);  //点击后再运行插件内容（firefox14+）?经常遇到网页卡死，绝大部分都是与flash有关, 这个参数可以减少假死
	user_pref("security.dialog_enable_delay", 0);  //扩展安装等待时间?毫秒；参考： 关闭扩展安装延迟
	user_pref("media.autoplay.enabled", false);  //启用媒体自动播放？
	//user_pref("pdfjs.disabled", true);  //禁用默认pdf解析功能? 是，用SumatraPDF
	user_pref("plugins.hide_infobar_for_missing_plugin", true);//禁止提示“缺少插件”的提示
	user_pref("plugin.default_plugin_disabled", true);//禁用“Mozilla默认插件”？
	//“Mozilla默认插件”是npnul32.dll文件，用处是用来警告你下载缺失的插件
	user_pref("toolkit.telemetry.rejected", true); //禁用帮助改进firefox 弹窗？
	//user_pref("extensions.checkCompatibility", false); // 不根据版本检测扩展兼容性.false表示静默升级的扩展，默认兼容，
	
	//扩展-------------------------------------------------------------
	//user_pref("extensions.getAddons.cache.enabled", false);//扩展管理器打开时会根据你已安装的扩展先你推荐扩展，这需要每天先mozilla发送一些信息来更新推荐列表，其实这些推荐大部分是我们不用的，可以直接禁用
	
	//浏览数据-------------------------------------------------------------
	user_pref("privacy.clearOnShutdown.siteSettings",true);//站点设置？绝不要删除，站点权限设置很有用
	       
	//加密SSl+证书-------------------------------------------------------------
	user_pref("browser.xul.error_pages.expert_bad_cert", true);//显示SSL证书错误页的“添加例外”按钮？默认false，
	       
	//更新+升级-------------------------------------------------------------
	user_pref("browser.search.update",false);//搜索引擎自动更新？
	user_pref("extensions.update.enabled",false);//开启扩展自动更新？
	user_pref("extensions.update.autoUpdateDefault",false);//自动更新扩展？
	       
	//书签-------------------------------------------------------------
	user_pref("browser.bookmarks.max_backups",2);//最多自动备份？份书签，0即不自动备份
	       
	//鼠标滚动加速-------------------------------------------------------------
	user_pref("mousewheel.acceleration.start",5);//滚动几次后开启加速？默认-1，即关闭，
	user_pref("mousewheel.acceleration.factor",10);.//滚动加速倍数？默认10，
	       
	       
	       
	
	
	
	//以下为NS的参数---------------------------------------------------------------
	//NS-----------------
	user_pref("noscript.autoReload.allTabs", false);// 自动刷新全部标签？
	user_pref("noscript.sync.enabled", true);//开启noscript同步？ 该参数默认不存在 ，如果想关掉NoScript 自动更新 ，设为false
	user_pref("noscript.allowClipboard",true);//允许由外部剪贴板进行富文本richtext的复制粘贴？
	user_pref("noscript.allowLocalLinks", true);//允许链接打开本地文件？
	
	//刷新----------------
	user_pref("noscript.forbidBGRefresh", 3);//0 不拦截刷新 ；1 拦截非活动的黑名单网站刷新 ，默认 ；2 拦截非活动的白名单网站刷新 ；3 拦截非活动的黑白名单网站刷新 ；
	
	//书签+bookmarket ，油猴子脚本+扩展 --------------------
	//user_pref("noscript.forbidBookmarklets",false);//在不可信Page中，禁用书签脚本？默认false
	user_pref("noscript.allowURLBarJS", true);//允许地址栏输入的javascript: 或data: 格式的URLs （不管当前Page是否可信 ）？
	user_pref("noscript.allowBookmarkletImports",true);//允许Bookmarklet在执行时调用第三方脚本 （即使来自非可信Sites ）？默认true
	user_pref("noscript.allowURLBarImports",true);//同上 ，但针对地址栏输入的javascript: URLs或 data:URLs ？默认false
	
	//嵌入对象 -----------------
	user_pref("noscript.contentBlocker", true);//对信任的网站仍然应用这些限制 ，默认false
	user_pref("noscript.confirmUnblock", false);//允许嵌入对象时需要确认？默认true
	
	//框架拦截 ----------------
	user_pref("noscript.forbidFrames",true);//默认false ，
	//user_pref("noscript.forbidIFrames",true);//默认false ，拦截框架还有利于拦截浮动广告 ，
	user_pref("noscript.forbidMixedFrames", true);//默认true ，拦截Iframes 内的子frames ？
	//框架拦截方式 ：
	//1 非可信site内的Iframe内容 ，始终拦截 ，除非其包含的内容来自与其所在page相同site ；
	//2 可信site内的Iframe的内容 ，如果来自非可信site就拦截 ，否则不拦截
	//3 任何时候 ，只要Iframe的内容来自与其父page相同的site ，都不拦截* ；下面的参数负责对Iframe拦截级别的调整 ：
	user_pref("noscript.forbidIFramesContext", 3);
	//拦截Iframe的级别？默认3 ；
	//0 拦截所有Iframe ，即使其中的内容来自与其父page相同的site ；
	//1 拦截网址与其父page不同的Iframe
	//2 拦截主域名与其父page不同的Iframe ；
	//3 拦截二级域名与其父page不同的Iframe ，有些用户在可信site依然拦截插入对象 ；
	
	//强制SSL/HTTPS----------------------------
	user_pref("noscript.allowHttpsOnly",0);//仅允许来自SSL加密的网站？0 从不；1 尽在使用tor时；2 总是；
	user_pref("noscript.httpsForced","*.google.com.hk\n*.google.com");//强制使用SSL的网站，\n表示换行
	//user_pref("noscript.httpsForced","*.google.com.hk *.google.com");//同上，当时仅用空格隔开，未换行，两种书写格式都可以
	user_pref("noscript.httpsForcedExceptions","*.115.com");//强制不使用SSL的网站，书写规则同上
	
	//Anti-XSS --------------------
	user_pref("noscript.xss.trustTemp", false);//视临时允许Sites为可信Sites ？
	user_pref("noscript.injectionCheck", 3);//注入检测器检测哪些请求？0 从不检查 ；1 检查从临时信任Sites的所有跨站-Cross-Sites 请求 ；2 检查所有跨站请求 ，默认 ；3 检查所有请求
	
	//GET与POST ， -----------------------
	user_pref("noscript.filterXGet", true);//净化可疑跨站请求？即剥离HTTP请求中的URL和Referer头中潜在的危险字符 （可能被用来注入恶意JS代码 ）
	user_pref("noscript.filterXPost", true);//将跨站请求方式从POST转为GET ？
	
	//外观通知 -------------------------------
	user_pref("noscript.hoverUI",false);//鼠标悬停图标时自动弹簇菜单列表？
	user_pref("noscript.showAbout", false);//关于... （版本号）
	
