Tidy Data
================
Kristal Quispe
9/27/2019

## Wide to long

``` r
pulse_data = 
  haven::read_sas("./data/public_pulse_data.sas7bdat") %>% 
  janitor::clean_names() %>% 
  pivot_longer(
    bdi_score_bl:bdi_score_12m,
    names_to = "visit", 
    names_prefix = "bdi_score_",
    values_to = "bdi"
  ) %>%
  mutate(
    visit = recode(visit, "bl" = "00m")
  )
```

## Seperate in litters

``` r
litters_data=
  read.csv("./data/FAS_litters.csv")%>% 
  janitor::clean_names() %>% 
  separate(col = group, into =c("dose", "day_of_tx"),3)
```
