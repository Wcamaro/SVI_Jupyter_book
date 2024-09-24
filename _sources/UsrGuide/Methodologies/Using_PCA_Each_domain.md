# Using_PCA_Each_domain
Using PCA of each domain to find the weight coefficient based on correlation between member of domain. And then using mean of each domain PCA as final vulnerability

```
##############
### Domain ###
##############
# copy to new new data set
personsDataN_logrono_PCA_Domain <- personsDataN_logrono
### Domain - Age 
#ageIndicators <- subset(personsDataN_logrono, select=c('c_ab0t4_pct_Z', 'c_ag0t4_pct_Z', 'c_amo75_pct_Z', 'c_afo75_pct_Z'))
ageIndicators <- subset(personsDataN_logrono, select=c('c_ab0t4_pct_N', 'c_ag0t4_pct_N', 'c_amo75_pct_N', 'c_afo75_pct_N'))
#cov(personsDataZ_logrono[,2:ncol(personsDataZ_logrono)])
cor(ageIndicators)
pca_model_ageDomain <- prcomp(ageIndicators,scale = TRUE)

##,centered = TRUE)
summary(pca_model_ageDomain)
#screeplot(pca_model_ageDomain,type = "lines")

#plot(pca_model_ageDomain$x,xlim= c(-4.,5.5), ylim = c(-4.,5.5))
#text(pca_model_ageDomain$x,labels = rownames(ageIndicators),adj = c(0.3,-0.5),cex = 0.1) 
#abline(v = 0 ,h = 0)

prpotion_variance_age<- summary(pca_model_ageDomain)$importance[2,]
ageDomain_pca_pr <- sweep(pca_model_ageDomain$x[,1:ncol(ageIndicators)], 2, unlist(prpotion_variance_age), "*")
# apply Normilize_values function to normilize PCs values
ageDomain_pca_pr[,1:4] <- apply(ageDomain_pca_pr[,1:4],2, Normilize_values)
personsDataN_logrono_PCA_Domain$ageDomain_pca <- rowMeans(ageDomain_pca_pr, na.rm = TRUE)

# just for checking
ageDomain_mean <- rowMeans(ageIndicators, na.rm = TRUE)
# just to compare 
print(paste('mean of age domain', ageDomain_mean, 'pca of agedomain',personsDataN_logrono_PCA_Domain$ageDomain_pca ))
```

```
# the above process for age domain should repeat for each domain 
# then the mean of all PCA of each domain can be considred ad vulrenability index
```