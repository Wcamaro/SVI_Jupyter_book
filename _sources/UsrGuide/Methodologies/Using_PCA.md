# Using_PCA
Using PCA of all indicators to find the weight coefficient of each indicators based on correlation between each indicators. 

```
#to extract the normilized indicators define st and end as follows:
st = 16
end = ncol(personsDataN_logrono) -2 # should be 29 
end
pca_model_all <- prcomp(personsDataN_logrono[,st:end],scale = TRUE)

##,centered = TRUE)
summary(pca_model_all)
screeplot(pca_model_all,type = "lines")

plot(pca_model_all$x,xlim= c(-4.,5.5), ylim = c(-4.,5.5))
text(pca_model_all$x,labels = rownames(personsDataN_logrono),adj = c(0.3,-0.5),cex = 0.1) 
abline(v = 0 ,h = 0)
```

```
allIndicators <- subset(personsDataN_logrono, select=c(st:end))
print(names(allIndicators))
# propotion variance associated to each PCs can be considered as weight of that PC
prpotion_variance <- summary(pca_model_all)$importance[2,]

#multiply each column by proportion varianve (each indicators multiply by weighted cofficent)
# there are 14 PCs 
pca_pr <- sweep(pca_model_all$x[,1:14], 2, unlist(prpotion_variance), "*")
#print(pca_pr)
# apply Normilize_values function to normilize PCs values
pca_pr[,1:14] <- apply(pca_pr[,1:14],2, Normilize_values)
#personsDataZ_logrono_PCA <- cbind(personsDataZ_logrono,pca_model_all$x[,1:14])
# if you wish to have step by step calculation uncomment the following line
#personsDataN_logrono_PCA <- cbind(personsDataN_logrono,pca_pr)

personsDataN_logrono$pca_all <- rowMeans(pca_pr, na.rm = TRUE)
#personsDataNZ_logrono$pca_all <- Normilize_values(personsDataNZ_logrono$pca_all)

# compare these three method results
print(paste('mean of all', personsDataN_logrono$meanall, 'weighted mean', personsDataN_logrono$mean_weigth,
            'pca of all',personsDataN_logrono$pca_all ))
```

```
## output the data as a csv as a backup 
## if you decied which method to use save in 3_output subdurectory
outputFile <- file.path(pipelineDir,"Vul_data_2021_logrono_3method.csv")
write.csv(personsDataN_logrono, outputFile, row.names = FALSE)
```


