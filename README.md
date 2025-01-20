# age-specific-migration-rates
Plotting age-specific migration rates

library(ggplot2)

# Load the data
migr <- read.csv("C:/Users/pnits/Downloads/migr (1).csv")
migr2 <- read.csv("C:/Users/pnits/Downloads/migr2 (1).csv")

```

```{r}
# Calculate age-specific in- and out-migration rates
migr$InRateA <- (migr$InA / migr$PopA) * 1000
migr$OutRateA <- (migr$OutA / migr$PopA) * 1000
migr$InRateB <- (migr$InB / migr$PopB) * 1000
migr$OutRateB <- (migr$OutB / migr$PopB) * 1000

# Plotting age-specific migration rates for Population A
ggplot(migr, aes(x = Age)) +
  geom_line(aes(y = InRateA, color = "In-Migration Rate A")) +
  geom_line(aes(y = OutRateA, color = "Out-Migration Rate A")) +
  labs(title = "Age-Specific Migration Rates for Population A",
       x = "Age", y = "Migration Rate (per 1000)") +
  scale_color_manual(values = c("In-Migration Rate A" = "blue", 
                                 "Out-Migration Rate A" = "red")) +
  theme_minimal()

# Plotting age-specific migration rates for Population B
ggplot(migr, aes(x = Age)) +
  geom_line(aes(y = InRateB, color = "In-Migration Rate B")) +
  geom_line(aes(y = OutRateB, color = "Out-Migration Rate B")) +
  labs(title = "Age-Specific Migration Rates for Population B",
       x = "Age", y = "Migration Rate (per 1000)") +
  scale_color_manual(values = c("In-Migration Rate B" = "green", 
                                 "Out-Migration Rate B" = "orange")) +
  theme_minimal()
