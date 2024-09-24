# Mean_of_all_Indicators
All indicators effect equally so Vul_Mean = ((〖Ind〗_1+〖Ind〗_2+⋯.+ 〖Ind〗_n  ))/n   where Ind is indicator 1 to n, and n is total number of indicators

```
# first method mean of all nrmilized indicators
ncol(personsDataN_logrono)
allIndicators <- subset(personsDataN_logrono, select=c(16:ncol(personsDataN_logrono)))
personsDataN_logrono$meanall <- rowMeans(allIndicators, na.rm = TRUE)
```

