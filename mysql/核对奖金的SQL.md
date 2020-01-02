#核对顾客极差
SELECT a.dist_no,a.bonus_amount,b.bonus_amount FROM bns_db.`bns_reward_cust_diff_bonus_201910`AS a ,test_data.bns_reward_cust_diff_bonus_201910 AS b
WHERE a.dist_no=b.dist_no AND a.bonus_amount<>CAST(b.bonus_amount AS DECIMAL(10,2));
SELECT dist_no,bonus_amount FROM bns_reward_cust_diff_bonus_201910 WHERE dist_no NOT in (SELECT dist_no FROM test_data.bns_reward_cust_diff_bonus_201910);
SELECT dist_no ,bonus_amount FROM test_data.bns_reward_cust_diff_bonus_201910 WHERE bonus_amount>0 AND dist_no not in (SELECT dist_no FROM bns_reward_cust_diff_bonus_201910);
-- 误差的370.86 是0000000的
SELECT SUM(bonus_amount) FROM bns_reward_cust_diff_bonus_201910;
SELECT SUM(bonus_amount) FROM test_data.bns_reward_cust_diff_bonus_201910;

#核对直销员奖励  数据一致
SELECT a.dist_no,b.dist_no,a.bonus_amount,b.bonus_amount as hx FROM bns_db.`bns_reward_dist_bonus_201910` AS a ,test_data.bns_reward_dist_bonus_201910 AS b
WHERE a.dist_no=b.dist_no AND a.bonus_amount<>CAST(b.bonus_amount AS DECIMAL(10,2));

SELECT COUNT(1) FROM bns_reward_dist_bonus_201910 where bonus_amount>0;
SELECT COUNT(1) FROM test_data.bns_reward_dist_bonus_201910 WHERE bonus_amount>0;
SELECT sum(bonus_amount) FROM bns_reward_dist_bonus_201910 ;
SELECT sum(bonus_amount) FROM test_data.bns_reward_dist_bonus_201910;

SELECT dist_no,bonus_amount FROM test_data.bns_reward_dist_bonus_201910 WHERE bonus_amount>0 AND dist_no not in(SELECT dist_no from bns_reward_dist_bonus_201910 WHERE bonus_amount>0);
SELECT dist_no ,bonus_amount from bns_reward_dist_bonus_201910 WHERE bonus_amount>0 AND dist_no not in(SELECT dist_no FROM test_data.bns_reward_dist_bonus_201910 WHERE bonus_amount>0);

#核对直销员极差  数据一致
SELECT a.dist_no,a.bonus_amount,b.bonus_amount FROM bns_db.`bns_reward_dist_diff_bonus_201910` AS a , test_data.bns_reward_dist_diff_bonus_201910 AS b
WHERE a.dist_no=b.dist_no AND a.bonus_amount<>CAST(b.bonus_amount AS DECIMAL(10,2)) AND a.bonus_amount>0;

SELECT COUNT(1) FROM bns_reward_dist_diff_bonus_201910 where bonus_amount>0;
SELECT COUNT(1) FROM test_data.bns_reward_dist_diff_bonus_201910 WHERE bonus_amount>0;
SELECT sum(bonus_amount) FROM bns_reward_dist_diff_bonus_201910 ;
SELECT sum(bonus_amount) FROM test_data.bns_reward_dist_diff_bonus_201910;


#核对红宝石奖 数据一致
SELECT a.dist_no,a.bonus_amount, b.bonus_amount  FROM bns_db.`bns_reward_ruby_bonus_201910` AS a,test_data.bns_reward_ruby_bonus_201910 AS b 
WHERE a.`dist_no`=b.dist_no AND a.bonus_amount<>CAST(b.bonus_amount AS DECIMAL(10,2));

SELECT COUNT(1) FROM bns_reward_ruby_bonus_201910 where bonus_amount>0;
SELECT COUNT(1) FROM test_data.bns_reward_ruby_bonus_201910 WHERE bonus_amount>0;
SELECT sum(bonus_amount) FROM bns_reward_ruby_bonus_201910;
SELECT sum(bonus_amount) FROM test_data.bns_reward_ruby_bonus_201910;

#核对翡翠奖 数据一致
SELECT a.dist_no,a.bonus_amount, b.bonus_amount  FROM bns_db.`bns_reward_emerald_bonus_201910`AS a,test_data.bns_reward_emerald_bonus_201910 AS b 
WHERE a.`dist_no`=b.dist_no AND a.bonus_amount=CAST(b.bonus_amount AS DECIMAL(10,2)) AND a.bonus_amount>0;

SELECT COUNT(1) FROM bns_reward_emerald_bonus_201910 where bonus_amount>0;
SELECT COUNT(1) FROM test_data.bns_reward_emerald_bonus_201910 WHERE bonus_amount>0;
SELECT sum(bonus_amount) FROM bns_reward_emerald_bonus_201910;
SELECT sum(bonus_amount) FROM test_data.bns_reward_emerald_bonus_201910;

#核对钻石奖 数据一致
SELECT  a.dist_no,a.bonus_amount, b.bonus_amount FROM bns_db.`bns_reward_diamond_bonus_201910`AS a,test_data.bns_reward_diamond_bonus_201910 AS b 
WHERE a.`dist_no`=b.dist_no AND a.bonus_amount<>CAST(b.bonus_amount AS DECIMAL(10,2)) AND a.bonus_amount>0;

SELECT COUNT(1) FROM bns_reward_diamond_bonus_201910 where bonus_amount>0;
SELECT COUNT(1) FROM test_data.bns_reward_diamond_bonus_201910 WHERE bonus_amount>0;
SELECT sum(bonus_amount) FROM bns_reward_diamond_bonus_201910;
SELECT sum(bonus_amount) FROM test_data.bns_reward_diamond_bonus_201910;

#核对金钻奖 数据一致
SELECT a.dist_no,a.bonus_amount, b.bonus_amount  FROM bns_db.`bns_reward_gold_dia_bonus_201910`AS a,test_data.bns_reward_gold_dia_bonus_201910 AS b 
WHERE a.`dist_no`=b.dist_no AND a.bonus_amount=CAST(b.bonus_amount AS DECIMAL(10,2)) AND a.bonus_amount>0;

SELECT COUNT(1) FROM bns_reward_gold_dia_bonus_201910 where bonus_amount>0;
SELECT COUNT(1) FROM test_data.bns_reward_gold_dia_bonus_201910 WHERE bonus_amount>0;
SELECT sum(bonus_amount) FROM bns_reward_gold_dia_bonus_201910;
SELECT sum(bonus_amount) FROM test_data.bns_reward_gold_dia_bonus_201910;

#核对平级奖 数据一致
SELECT a.dist_no,a.bonus_amount,b.bonus_amount,a.bonus_amount-b.bonus_amount as 误差 FROM bns_db.bns_reward_golden_opv_bonus_201910 AS a ,test_data.bns_reward_golden_opv_bonus_201910 AS b
WHERE a.dist_no=b.dist_no AND a.bonus_amount<>CAST(b.bonus_amount AS DECIMAL(10,2))  AND a.bonus_amount>0 ORDER BY 误差;
SELECT a.dist_no,a.bonus_amount,b.bonus_amount,a.bonus_amount-b.bonus_amount as 误差 FROM bns_db.bns_reward_golden_opv_bonus_201910 AS a ,test_data.bns_reward_golden_opv_bonus_201910 AS b
WHERE a.dist_no=b.dist_no AND a.bonus_amount=CAST(b.bonus_amount AS DECIMAL(10,2))  AND a.bonus_amount>0 ORDER BY 误差;

SELECT COUNT(1) FROM bns_reward_golden_opv_bonus_201910 where bonus_amount>0;
SELECT COUNT(1) FROM test_data.bns_reward_golden_opv_bonus_201910 WHERE bonus_amount>0;
SELECT sum(bonus_amount) FROM bns_reward_golden_opv_bonus_201910;
SELECT sum(bonus_amount) FROM test_data.bns_reward_golden_opv_bonus_201910;

#核对双金钻的0.1%    数据一致
SELECT a.dist_no,a.bonus,b.bonus FROM bns_db.`bns_reward_2gdiamond_bonus_1`AS a ,test_data.bns_reward_2gdiamond_bonus_1 AS b
WHERE a.dist_no=b.dist_no AND a.bonus_month ='201910' AND a.bonus = CAST(b.bonus AS DECIMAL(10,2)) ;
SELECT a.dist_no,a.bonus,b.bonus,a.bonus-b.bonus FROM bns_db.`bns_reward_2gdiamond_bonus_1`AS a ,test_data.`bns_reward_2gdiamond_bonus_1` AS b
WHERE a.dist_no=b.dist_no AND a.bonus_month='201910' and b.bonus_month='201910' AND a.bonus <>b.bonus ; 

SELECT COUNT(1) FROM bns_reward_2gdiamond_bonus_1 where bonus_month='201910' and bonus>0;
SELECT COUNT(1) FROM test_data.bns_reward_2gdiamond_bonus_1 where bonus_month='201910' and bonus>0;
SELECT SUM(bonus) FROM bns_reward_2gdiamond_bonus_1 where bonus_month='201910' and bonus>0;
SELECT SUM(bonus) FROM test_data.bns_reward_2gdiamond_bonus_1 where bonus_month='201910' and bonus>0;

#核对双金钻的0.3%   数据一致


SELECT a.dist_no,a.bonus,b.bonus,a.bonus-b.bonus FROM bns_db.`bns_reward_2gdiamond_bonus_2`AS a ,test_data.`bns_reward_2gdiamond_bonus_2` AS b
WHERE a.dist_no=b.dist_no AND a.bonus_month='201910' and b.bonus_month='201910' AND a.bonus <>b.bonus ; 


SELECT COUNT(1) FROM bns_reward_2gdiamond_bonus_2 where bonus_month='201910';
SELECT COUNT(1) FROM test_data.bns_reward_2gdiamond_bonus_2 WHERE  bonus_month='201910';
SELECT SUM(bonus) FROM bns_reward_2gdiamond_bonus_2 WHERE bonus_month='201910';
SELECT SUM(bonus) FROM test_data.bns_reward_2gdiamond_bonus_2 WHERE bonus_month='201910';

#核对双金钻的2重


SELECT a.dist_no,a.bonus,b.bonus as '完美',b.bonus-a.bonus FROM bns_db.`bns_reward_2gdiamond_bonus_3`AS a ,
test_data.bns_reward_2gdiamond_bonus_3 AS b
WHERE a.dist_no=b.dist_no AND a.type=2 and b.type='2' AND a.bonus_month='201910' AND b.bonus_month='201910'and a.bonus<>b.bonus ;

select * from bns_reward_2gdiamond_bonus_3 where type = '2';

SELECT COUNT(1) FROM bns_reward_2gdiamond_bonus_3 where bonus_month='201910' AND type=2;
SELECT COUNT(1) FROM test_data.bns_reward_2gdiamond_bonus_3 WHERE bonus_month='201910' AND type=2;
SELECT SUM(bonus) FROM bns_reward_2gdiamond_bonus_3 WHERE bonus_month='201910' AND type=2;
SELECT SUM(bonus) FROM test_data.bns_reward_2gdiamond_bonus_3 WHERE bonus_month='201910' AND type=2;


#核对双金钻的3重


SELECT a.dist_no,a.bonus as '联调',b.bonus as '完美',b.bonus-a.bonus FROM bns_db.`bns_reward_2gdiamond_bonus_3`AS a ,test_data.bns_reward_2gdiamond_bonus_3 AS b
WHERE a.dist_no=b.dist_no AND a.type=3 and b.type='3' AND a.bonus_month='201910' and b.bonus_month='201910' AND a.bonus<>b.bonus ;


SELECT a.dist_no,a.bonus as '联调',b.bonus as '完美',b.bonus-a.bonus FROM bns_db.`bns_reward_2gdiamond_bonus_3`AS a ,test_data.bns_reward_2gdiamond_bonus_3 AS b
WHERE a.dist_no=b.dist_no AND a.type=3 and b.type='3' AND a.bonus_month='201910' and b.bonus_month='201910' AND a.bonus=b.bonus ;


SELECT COUNT(1) FROM bns_reward_2gdiamond_bonus_3 where bonus_month='201910' AND type=3;
SELECT COUNT(1) FROM test_data.bns_reward_2gdiamond_bonus_3 where bonus_month='201910' AND type=3;
SELECT SUM(bonus) FROM bns_reward_2gdiamond_bonus_3 where bonus_month='201910' AND type=3;
SELECT SUM(bonus) FROM test_data.bns_reward_2gdiamond_bonus_3 where bonus_month='201910' AND type=3;

#核对双金钻的4重


SELECT a.dist_no,a.bonus,b.bonus,b.bonus-a.bonus FROM bns_db.`bns_reward_2gdiamond_bonus_3`AS a ,test_data.bns_reward_2gdiamond_bonus_3 AS b
WHERE a.dist_no=b.dist_no AND a.type=4 and b.type='4'AND b.bonus_month='201910'and a.bonus_month='201910' AND a.bonus=b.bonus ;


SELECT COUNT(1) FROM bns_reward_2gdiamond_bonus_3 where bonus_month='201910' AND type=4;
SELECT COUNT(1) FROM test_data.bns_reward_2gdiamond_bonus_3 where bonus_month='201910' AND type=4;
SELECT SUM(bonus) FROM bns_reward_2gdiamond_bonus_3 WHERE bonus_month='201910' AND type=4;
SELECT SUM(bonus) FROM test_data.bns_reward_2gdiamond_bonus_3 WHERE bonus_month='201910' AND type=4;;


#三金钻
SELECT a.dist_no ,a.bonus_amount,b.sgje+b.sgje1 FROM bns_reward_triple_golden_bonus a , test_data.bns_reward_cust_diff_bonus_201910 b 
WHERE a.dist_no = b.dist_no AND a.bonus_month = '201910';

#核对OPV
SELECT a.dist_no,a.level_no,a.opv,b.yxzjf FROM bns_db.bns_indv_performance_master_201910 a INNER JOIN test_data.p11902 b
ON a.`dist_no` = b.dist_no AND a.`opv` <> b.`yxzjf` ORDER BY a.level_no DESC;

SELECT a.dist_no,a.ppv,b.grjf FROM bns_db.bns_indv_performance_master_201910 a INNER JOIN test_data.p11902 b
ON a.`dist_no` = b.dist_no AND a.`ppv` <> b.`grjf`;

SELECT a.dist_no,a.level_no,a.gpv,b.xzjf FROM bns_db.bns_indv_performance_master_201910 a INNER JOIN test_data.p11902 b
ON a.`dist_no` = b.dist_no AND a.`gpv` <> b.`xzjf` AND a.pin>=5  ORDER BY a.level_no DESC;

#查找出存在pv表，不存在uplink表
SELECT * FROM bns_uplink WHERE level_no IS NULL;
SELECT * FROM bns_pv WHERE dist_no NOT IN (SELECT dist_no FROM bns_uplink); 

