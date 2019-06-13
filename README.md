# FitSleepBeta
Fitbit devices have been increasingly used in scientific studies to measure sleep outcomes. Nevertheless, validation studies show that these devices are not accurate. This project aims to design computational models that can be used to post-process Fitbit data for accurate sleep measurements (as close as possible to medical devices). 

The data that you can download here were collected using a Fitbit Charge 2 and a medical-grade device (SleepScope, single channel portable EEG) concurrently from 23 healthy young adults. The medical data were used as the ground truth. Informed consent was obtained from the participants to share the data under proper anonymization. 

In sleep science, a whole night's data are usually cut into short intervals called epochs. The AASM standard recommends 30s as the window size of each interval; an 8h sleep therefore consists of 960 epochs. Sleep staging is then conducted epoch-by-epoch sliding from the beginning to the end of the sleep. 

In the datasets, each sample corresponds to an epoch in that night's sleep of that participant; an 8h sleep consists of 960 epochs and therefore will generate 960 samples in the dataset. The total number of epochs differs from person to person as their total sleep time was different. Each dataset consists of labels and 20 features. There is no missing data and no wrong data. Some explanations of the columns.

- colomn A (label): the sleep stage measured with the medical device in epoch t
- column B (epoch): the ID of epoch t, e.g. epoch 1 is 1, epoch 2 is 2, etc
- column C (fitbit_sleep_t): the sleep stage measured with Fitbit Charge 2 in epoch t
- column D (fitbit_hr): the average heart rate measured with Fitbit Charge 2 in epoch t
- column E (delta_hr_t): [fitbit_hr(t)-fitbit_hr(t-1)]/fitbit_hr(t-1)
- column F (sex): the gender of the participant
- column G (age): the age of the participant
- column H (total_sleep_time_min): the total amount of sleep time in minutes the participant had that night measured with Fitbit Charge 2 
- column I (total_wake_time_min): the total amount of wakefulness time in minutes the participant had that night measured with Fitbit Charge 2
- column J (sleep_efficiency): the sleep efficiency measured with Fitbit Charge 2, total_sleep_time_min/(total_sleep_time_min + total_wake_time_min)
- column K (wake_ratio): the ratio of wakefulness measured by Fitbit Charge 2, total_wake_time_min / (total_sleep_time_min + total_wake_time_min)
- column L (light_ratio): the ratio of light sleep measured by Fitbit Charge 2, light_sleep_time_min / (total_sleep_time_min + total_wake_time_min)
- columne M (deep_ratio): the ratio of deep sleep measured by Fitbit Charge 2, deep_sleep_time_min / (total_sleep_time_min + total_wake_time_min)
- columne N (REM_ratio): the ratio of REM sleep measured by Fitbit Charge 2, REM_sleep_time_min / (total_sleep_time_min + total_wake_time_min)
- columne O (PSQI): Pittsburgh Sleep Quality Index measured by PSQI questionnaire, PSQI >= 5 is indicative of poor sleep
- columne P (fitbit_sleep_t-1): the sleep stage of epoch (t-1) measured by Fitbit Charge 2
- columne Q (fitbit_sleep_t-2): the sleep stage of epoch (t-2) measured by Fitbit Charge 2
- columne R (fitbit_sleep_t-3): the sleep stage of epoch (t-3) measured by Fitbit Charge 2
- columne S (fitbit_sleep_t+1): the sleep stage of epoch (t+1) measured by Fitbit Charge 2
- columne T (fitbit_sleep_t+2): the sleep stage of epoch (t+2) measured by Fitbit Charge 2
- columne U (fitbit_sleep_t+3): the sleep stage of epoch (t+3) measured by Fitbit Charge 2

Current only 3 epochs before and after the current epoch are used as features. It's possible to consider more historical and future epochs into modelling. 

Macro-level features like sex, age, total sleep time, total wake time, sleep efficiency, wake ratio, light ratio, deep ratio, and REM ratio doesn't vary (ie. the values are the same in all samples) within a dataset. 
