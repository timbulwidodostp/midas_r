# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Regression Mixed Data Sampling (MIDAS) Use midas_r (midasr) With (In) R Software
install.packages("midasr")
library("midasr")
# Estimation Regression Mixed Data Sampling (MIDAS) Use midas_r (midasr) With (In) R Software
midas_r_y = read.csv("https://raw.githubusercontent.com/timbulwidodostp/midas_r/main/midas_r/midas_r_y.csv",sep = ";")
ts_midas_r_y <- ts(midas_r_y, start=c(1948), frequency=1)
midas_r_x = read.csv("https://raw.githubusercontent.com/timbulwidodostp/midas_r/main/midas_r/midas_r_x.csv",sep = ";")
ts_midas_r_x <- ts(midas_r_x, start=c(1948), frequency=12)
Y <- diff(log(ts_midas_r_y))
X <- window(diff(midas_r_x), start = 1949)
trend <- 1:length(Y)
midas_r_1 <- midas_r(Y ~ trend + mls(Y, 1, 1) + fmls(X, 11, 12, nealmon), start = list(X = rep(0, 3)))
summary(midas_r_1)
midas_r_2 <-  midas_r(Y ~ trend + mls(Y, 1, 1, "*") + fmls(X, 11, 12, nealmon), start = list(X = rep(0, 3)))
summary(midas_r_2)
# Regression Mixed Data Sampling (MIDAS) Use midas_r (midasr) With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished