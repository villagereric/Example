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
