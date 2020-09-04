# UFCFightPrediction

Goal is to try to predict Fight Results with as high a percentage of accuracy as possible using only fighters Stats

This is done by weighting stats depending on how often a winner had an advantage then multiplying this by the advantage a fighter would have in this stat

e.g if fighter1 has a higher score in a stat (fighter1num - fighter2num)/(fighter1num + fighter2num) * Weight

Weight is calculated by (totalnumber of winners who had a higher stat)/ (Total amount of combined Stats)

tweaks will be made for combined higher stats to try and get better results
