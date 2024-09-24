# Weighted_mean
to allow the indictors effect differently (weight based on number of indicators of each domain, e.g. the domain with one indicator has weight = 1 and age domain indicators with 4 indicators have weight = 0.25) so 
Vul_WM = ((〖Ind〗_1* W_1+〖Ind〗_2* W_(2 )+⋯.+ 〖Ind〗_n* W_n  ))/n   where W is a weight coefficient for each indicators.


```
#function to find the weigth of each indicators based on number of indicator in each domain
get_weight <- function(var){
    Domains = list(ageDomain,healthDomain, mobilityDomain, incomeDomain, socialNetworkDomain
            ,localKnowledgeDomain,tenureDomain,income_cu_7500_26)
    for (df in Domains){
        if (var %in% names(df))
            #return the nuber on indicators of a domain
            return(round(1/(ncol(df)-1),2))
    }
    # return zero means giving 0 weirht and not consider it as indicator if not belong to any domain 
    # or you can change this to 1 to give weight of one and consider it as a indicator even not belongs to any domain.
    # this depends on your decision
    return(0) 
}
## function to calculate the lenght of variable x -6 (witout '_pct_N')
nchar_6 <- function(x){
    return(nchar(x) -6)
}
```

```
# second method weighted mean 
# this is based on number of each domin members for example 0.25 weigt for domin with 4 indicators
# find the number of member of each domin
st <- 16
end <- ncol(personsDataN_logrono)-1
# find lenght of each standard indicators name (witout '_pct_N')
l_var <- lapply(names(personsDataN_logrono[st:end]),nchar_6)
# find weigth cofficient of each indicators
var_weight <- 
lapply(substr(names(personsDataN_logrono[st:end]),1,l_var),get_weight)
print(paste('indicator: ',substr(names(personsDataN_logrono[st:end]),1,l_var), 'weight:  ',var_weight))
#print(substr(names(personsDataN_logrono[st:end]),1,l_var),var_weight )
#mean_weight <- sweep($x[,1:14], 2, unlist(prpotion_variance), '*')
```

```
#personsDataN_logrono[st:end]
mean_weight <- sweep(personsDataN_logrono[st:end], 2, unlist(var_weight), "*")
#mean_weight
# if you want to keep step by step calculation uncomment the following line
#personsDataN_logrono <- cbind(personsDataN_logrono,mean_weight)
# calculate mean of weighted indicators
personsDataN_logrono$mean_weigth <- rowMeans(mean_weight, na.rm = TRUE)
# compare two methods mean all and mean weight method
print(paste('mean all: ',personsDataN_logrono$meanall, 'mean weight:  ',personsDataN_logrono$mean_weigth))
```

