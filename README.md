# Typemoon
R studying
library(dplyr) # 载入 dplyr 包，以便进行数据框操纵
pci_rate_clean <- read.csv("pci_rate_clean.csv") # 读入数据
pci_rate_clean_TF <- pci_rate_clean == 1 # 取值为1定义为TRUE，否则为FALSE
error_rate_p <- apply(pci_rate_clean_TF, 1, mean) # 求个体正确率，长度同个体数
error_rate_q <- apply(pci_rate_clean_TF, 2, mean) # 求每道题的正确率，长度同题目数
result <- bind_cols(pci_rate_clean, 
                    error_rate_p = error_rate_p) # 把个体正确率并入数据框
mean(result$error_rate_p > 0) # 计算至少做错一道误的个体占总体的比率
