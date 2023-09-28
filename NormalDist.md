# 假設人類的智商呈常態分配，平均智商m = 110分，標準差s = 10 分，求下列百分比
#(a) 123 分以上 (b) 95 分以上 (c)介於 100 分到 120 分之間 (d) 89 分以下
#(e)軍校錄取新生，智商分數為必要條件，若要求新生智商為前 20%，則智商分數最
#低錄取分數為多少？ 

import scipy.stats as stats

#平均智商
mean = 110

#標準差
std = 10

#建立一個標準常態分布※非函數
int_dist = stats.norm(loc=mean, scale=std)

#(a)智商高於123分以上的有多少百分比
probability_123up = int_dist.sf(123)
#轉換百分比
probability_123up_percent = probability_123up * 100


#(b)智商95分以上的有多少百分比
probability_95up = int_dist.sf(95)
#轉換百分比
probability_95up_percent = probability_95up * 100

#(c)介於100分到120分之間的百分比
probability_100_120 = int_dist.cdf(120) - int_dist.cdf(100)
#轉換百分比
probability_100_120_percent = probability_100_120 * 100

#(d)89分以下的百分比
probability_89down = int_dist.cdf(89)
#轉換百分比
probability_89down_percent = probability_89down * 100

#(e)若要求新生智商為前 20%，則智商分數最低錄取分數為多少？ 
pr = 0.2
lowest_score = int_dist.ppf(1 - pr) # or int_dist.isf(0.2)


print(f'智商高於123分以上的有:{probability_123up_percent:.2f}%')
print(f'智商高於95分以上的有:{probability_95up_percent:.2f}%')
print(f'智商高於介於100~120分以上的有:{probability_100_120_percent:.2f}%')
print(f'智商高於89分以下的有:{probability_89down_percent:.2f}%')
print(f'若要求新生智商為前 20%，則智商分數最低錄取分數為:{lowest_score:.2f} score')



#書上p.122 example 標準常態分配參數X~N(mu, std)

import scipy.stats as stats
from scipy.stats import norm

#如果男性身高平均為175cm，標準差6cm，那麼一名隨機挑選的男性身高為183cm的機率為多少
mean = 175
std = 6

#建立凍結分布
heightDist = stats.norm(loc=mean, scale=std)

#隨機挑一名男性身高為183cm的機率
probability_183up = heightDist.sf(183)
#轉換百分比
probability_183up_percent = probability_183up *100

print(f'隨機挑一名男性身高為183cm的機率:{probability_183up_percent:.2f}%')



#假設罐頭的標準差4g，那麼平均重量應該為多少，才可以確保99%的罐頭重量至少為250g?
std_can = 4
mean_weight = stats.norm.ppf(0.99, loc=250, scale=std_can)
print(f'平均重量至少為{mean_weight:.2f}g，才能確保99%罐頭重量是250g')

#男性平均身高為175cm，標準差6cm，女性身高平均為168cm，標準差3cm，那麼隨機挑選男姓比隨機挑選的女性身高還要矮的機率是多少?
man_mean = 175
man_std = 6
women_mean = 168
women_std = 3

#建立凍結分布
mdist = stats.norm(loc=man_mean, scale=man_std)
wdist = stats.norm(loc=women_mean, scale=women_std)

#隨機挑選男姓比隨機挑選的女性身高還要矮的機率
probability_manlow = mdist.cdf(women_mean)
#轉換百分比
probability_manlow_percent = probability_manlow *100


print(f'隨機挑選的男性比隨機挑選的女性身高還要矮的機率是{probability_manlow_percent:.2f}%')






