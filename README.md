# mysql-backup


#!/bin/sh

bseDir="/bak";

cd "$baseDir";

echo "开始备份数据库";

#开始备份mall_distribution数据库 http://moguit.cn/#/info?blogOid=117 mysql脚本备份

echo `mysqldump  -uroot -p'admin' --default-character-set=utf8  mall_distribution > mall_distribution_$(date +%Y%m%d).sql`;

#开始备份mall_goods数据库

echo `mysqldump  -uroot -p'admin' --default-character-set=utf8  mall_goods > mall_goods_$(date +%Y%m%d).sql`;

#开始备份mall_member数据库

echo `mysqldump  -uroot -p'admin' --default-character-set=utf8  mall_member > mall_member_$(date +%Y%m%d).sql`;


#开始备份mall_statistics数据库

echo `mysqldump  -uroot -p'admin' --default-character-set=utf8  mall_statistics > mall_statistics_$(date +%Y%m%d).sql`;


#开始备份mall_system数据库

echo `mysqldump  -uroot -p'admin' --default-character-set=utf8  mall_system > mall_system_$(date +%Y%m%d).sql`;


#开始备份mall_trade数据库

echo `mysqldump  -uroot -p'admin' --default-character-set=utf8  mall_trade > mall_trade_$(date +%Y%m%d).sql`;


echo "正在进行备份文件打包"

echo `tar zcvf mall_distribution_$(date +%Y%m%d).tar.gz  mall_goods_$(date +%Y%m%d).sql mall_member_$(date +%Y%m%d).sql mall_statistics_$(date +%Y%m%d).sql mall_system_$(date +%Y%m%d).sql mall_trade_$(date +%Y%m%d).sql`;

echo `rm -rf mall_distribution_$(date +%Y%m%d).sql`;

echo `rm -rf mall_goods_$(date +%Y%m%d).sql`;

echo `rm -rf mall_member_$(date +%Y%m%d).sql`;

echo `rm -rf mall_statistics_$(date +%Y%m%d).sql`;

echo `rm -rf mall_system_$(date +%Y%m%d).sql`;

echo `rm -rf mall_trade_$(date +%Y%m%d).sql`;

echo "备份数据完成";

oldDate=`date --date='8 day ago' +%Y%m%d`;

#删除当前日期-8的备份

echo `rm -rf mall_*_$oldDate*`;

echo "删除$oldDate的备份成功"