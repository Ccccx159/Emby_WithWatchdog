# Emby_WithWatchdog
## 简介
借助python中的看门狗模块（“watchdog”）监视emby媒体库目录，通过电报（telegram）的bot和channel，向频道订阅者推送Emby媒体库中新增影片信息，包括电影和剧集。

该方法基于 Emby Server 自动影片刮削生成的“xxxx.nfo”文件。影片新入库后，Emby Server 自动执行刮削生成xml格式的nfo文件，通过xmllint可以解析到部分该影片或者剧集的信息。而封面图片等信息，则需要通过tmdb资料库的api token进行查询获取。因此需依赖python中的“requests”模块，通过调用"get"方法获取完整信息。在按照电报bot的api文档对payload数据行组装后，调用post方法推送给bot，由bot发布至对应频道。

## 环境依赖
1. python3
2. python Module: *watchdog*, *requests* (cmd: `pip3 install watchdog requests`)
3. xmllint (os: ubuntu 20.04，cmd: `sudo apt-get install libxml2-utils`)

## 参数说明
| 参数 | 说明 |
| -- | -- |
| TG_BOT_TOKEN | 电报 bot token |
| TG_CHAT_ID | 电报频道 chat_id |
| TMDB_API_TOKEN | TMDB api token |

## 参考文档
+ tmdb api 文档：https://developers.themoviedb.org/4
+ telegram bot api 文档：https://core.telegram.org/bots/api
