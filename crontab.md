# Crontab

To open Crontab write `crontab -e`



## Best practice

So try and `cd` into the project in crontab and then run your commends. The reason is that running the command directly nearly always gives errors with environment variables, finding files, etc. 



## Examples

So I have this at the top of my crontab for some reason. I think it was to get all my environment variables working so i fx can reference `node` without specifying the specific location

```
PATH=PATH=/usr/local/sbin:/usr/local/bin:/usir/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/games
```



```
# m h  dom mon dow   command
# 00 16 * * * cd /home/YOUR_PROJECT && ./data-deploy.sh >>/home/YOUR_PROJECT/newest-log 2>&1
0 */2 * * * cd /home/YOUR_PROJECT && node ./YOUR_PROJECT.js >>/home/YOUR_PROJECT/newest-log 2>&1
```



## Time examples

16:00 every day

```
00 16 * * *
```

Every second hour

```bash
0 */2 * * *  /home/username/test.sh
```



## Write logs to a file

You can write the logs of your call like this after your command:

```
>>/home/YOUR_PROJECT/newest-log 2>&1
```

So this is piping the logs into the file `newest-log`