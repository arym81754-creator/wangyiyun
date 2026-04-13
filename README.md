# ==============================================
# QQ音乐 & 网易云音乐 全自动合集
# 功能：秒过广告领VIP + 自动签到 + 防跳转商店
# Quantumult X 自用脚本
# ==============================================

[rewrite_local]

# QQ音乐 广告秒过 + 自动领奖
^https?:\/\/.*qqmusic\.qq\.com\/(ad|report|reward|task|activity) url script-response-body https://cdn.jsdelivr.net/gh/ddgksf2013/Script/QQMusicAD.js

# QQ音乐 防跳转应用商店
^https?:\/\/.*\.qq\.com\/(adclick|adurl|jump) url reject-200
^https?:\/\/.*\.gtimg\.cn\/.*ad url reject-200

# 网易云音乐 广告秒过 + 自动领30分钟VIP
^https?:\/\/.*music\.163\.com\/weapi\/(ad|advert|play|reward) url script-response-body https://cdn.jsdelivr.net/gh/ddgksf2013/Script/NeteaseAD.js

# 网易云 广告域名拦截
^https?:\/\/.*ad\.163\.com.* url reject-200

# 通用拦截跳应用商店
^https?:\/\/.*\.apple\.com\/.*app url reject
^market:\/\/.* url reject
^intent:\/\/.* url reject

[task_local]

# QQ音乐 每日自动签到 08:00
0 8 * * * https://cdn.jsdelivr.net/gh/ddgksf2013/Script/QQMusicSign.js, tag=QQ音乐签到, enabled=true

# 网易云音乐 每日自动签到 08:05
5 8 * * * https://cdn.jsdelivr.net/gh/ddgksf2013/Script/NeteaseSign.js, tag=网易云签到, enabled=true

[mitm]
hostname = *.qqmusic.qq.com, *.qq.com, *.music.163.com, *.163.com, *.ad.163.com
