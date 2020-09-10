# UFCFightPrediction

Goal is to try to predict Fight Results with as high a percentage of accuracy as possible using only fighters Stats

This is done by weighting stats depending on how often a winner had an advantage then multiplying this by the advantage a fighter would have in this stat

e.g if fighter1 has a higher score in a stat (fighter1num - fighter2num)/(fighter1num + fighter2num) * Weight

Weight is calculated by (total number of winners who had a higher stat)/ (Total number of fights)

tweaks will be made for combined higher stats to try and get better results

# Time complexity for Card Finder

def page_url(url):
    headers = {"User-Agent": "Mozilla/5.0"}
    page = requests.get(url, headers=headers)
    soup: BeautifulSoup = BeautifulSoup(page.content, 'html.parser')
    return soup


class find_fighters_on_cards:

    fighter1 = [] O(1)
    fighter1link = [] O(1)
    fighter2 = [] O(1)
    fighter2link = [] O(1)
    card_link = [] O(1)

    def find_cards(list, url):
        url1 = page_url(url) O(1)
        cards = url1.find_all(class_='b-link b-link_style_black') O(1)
        for e in cards[0:10]: O(n)
            list.append((str(e).split('"'))[3]) O(1)
        return list O(1)

    find_cards(card_link, "http://www.ufcstats.com/statistics/events/completed?page=all")

    def find_card_info(list1, list2, list3, list4, list5):
        for e in list1: O(n)
            try:
                url1 = page_url(e) O(1)
                fighters = url1.find_all(class_='b-link b-link_style_black') O(1)
                for t in range(0, len(fighters), 2): O(n)
                    list4.append(str(fighters[t]).split('"')[3]) O(1)
                    list2.append(fighters[t].text) O(1)
                for y in range(1, len(fighters), 2): O(n)
                    list5.append(str(fighters[y]).split('"')[3]) O(1)
                    list3.append(fighters[y].text) O(1)
            except:
                continue O(1)

    find_card_info(card_link, fighter1, fighter2, fighter1link, fighter2link)
    
    O(1)*16 + O(n) + O(n^2) + O(n^2) 
    
    remove constants
    = O(n) + O(2n^2)
    highest growth rate
    = O(n^2)
    
    #For loop growth
    
                for k in range(len(Stats)):
                u5 = Stats[k].text.replace(' ', '').replace('\n', '').split(':')
                t5 = Stats2[k].text.replace(' ', '').replace('\n', '').split(':')
                if u5[0] == '':
                    u5 = ['0', '0']
                if t5[0] == '':
                    t5 = ['0', '0']
                if u5[1] == '--':
                    u5 = ['0', '0']
                if t5[1] == '--':
                    t5 = ['0', '0']
                if u5[1] == '0':
                    if u5[0] == '0':
                        u5 = ['0', '0']
                    else:
                        u5[1] = int(t5[1].replace('"', ''))/4
                if t5[1] == '0':
                   if t5[0] == '0':
                        t5 = ['0', '0']
                   else:
                        t5[1] = int((u5[1].replace('"', '')))/4
                if t5[0] == 'Weight':
                    if float((u5[1].split('l'))[0]) > float((t5[1].split('l'))[0]):
                        fighter11.append('Weight' + '+' + str((float((u5[1].split('l'))[0]) - float((t5[1].split('l'))[0])) / float((u5[1].split('l'))[0])))
                        Weight.append(float((u5[1].split('l'))[0]))
                    if float((t5[1].split('l'))[0]) > float((u5[1].split('l'))[0]):
                        fighter22.append('Weight' + '+' + str((float((t5[1].split('l'))[0]) - float((u5[1].split('l'))[0])) / float((t5[1].split('l'))[0])))
                if t5[0] == 'Reach':
                    if float(u5[1][0:2]) > float(t5[1][0:2]):
                        fighter11.append('Reach' + '+' + str((float(u5[1][0:2]) - float(t5[1][0:2])) / int(u5[1][0:2])))
                        Reach.append(float(u5[1][0:2]))
                    if float(t5[1][0:2]) > float(u5[1][0:2]):
                        fighter22.append('Reach' + '+' + str((float(t5[1][0:2]) - float(u5[1][0:2])) / float(t5[1][0:2])))
                if t5[0] == 'Height':
                    if float(u5[1].split('\'')[0]) > float(t5[1].split('\'')[0]):
                        fighter11.append('Height' + '+' + str((((float(u5[1].split('\'')[0])*12) + float(u5[1].split('\'')[1].replace('"', '')))
                            - ((float(t5[1].split('\'')[0])*12) + float(t5[1].split('\'')[1].replace('"', '')))) /
                            ((float(u5[1].split('\'')[0])*12) + float(u5[1].split('\'')[1].replace('"', '')))))
                        Height.append(u5[1])
                    if float(t5[1].split('\'')[0]) > float(u5[1].split('\'')[0]):
                        fighter22.append('Height' + '+' + str((((float(t5[1].split('\'')[0])*12) + float(t5[1].split('\'')[1].replace('"', '')))
                            - ((float(u5[1].split('\'')[0])*12) + float(u5[1].split('\'')[1].replace('"', '')))) /
                            ((float(t5[1].split('\'')[0])*12) + float(t5[1].split('\'')[1].replace('"', '')))))
                    if float(u5[1].split('\'')[0]) == float(t5[1].split('\'')[0]):
                        if float(u5[1].split('\'')[1].replace('"', '')) > float(t5[1].split('\'')[1].replace('"', '')):
                            fighter11.append('Height' + '+' + str((((float(u5[1].split('\'')[0])*12) + float(u5[1].split('\'')[1].replace('"', '')))
                                - ((float(t5[1].split('\'')[0])*12) + float(t5[1].split('\'')[1].replace('"', '')))) /
                                ((float(u5[1].split('\'')[0])*12) + float(u5[1].split('\'')[1].replace('"', '')))))
                            Height.append(u5[1])
                        if float(t5[1].split('\'')[1].replace('"', '')) > float(u5[1].split('\'')[1].replace('"', '')):
                            fighter22.append('Height' + '+' + str((((float(t5[1].split('\'')[0])*12) + float(t5[1].split('\'')[1].replace('"', '')))
                                - ((float(u5[1].split('\'')[0])*12) + float(u5[1].split('\'')[1].replace('"', '')))) /
                                ((float(t5[1].split('\'')[0])*12) + float(t5[1].split('\'')[1].replace('"', '')))))
                if t5[0] == 'SLpM':
                    if u5[1] > t5[1]:
                        fighter11.append('SLpM' + '+' + str(
                            (float(u5[1]) - float(t5[1])) / float(u5[1])))
                        SLpM.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('SLpM' + '+' + str(
                            (float(t5[1]) - float(u5[1])) / float(t5[1])))
                if t5[0] == 'Str.Acc.':
                    if u5[1] > t5[1]:
                        fighter11.append('Str.Acc.' + '+' + str((float('0.' + (u5[1]).replace('%', '')) - float('0.' + (t5[1]).replace('%', '')))
                                 / float('0.' + (u5[1]).replace('%', ''))))
                        Str_Acc.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('Str.Acc.' + '+' + str((float('0.' + (t5[1]).replace('%', '')) - float('0.' + (u5[1]).replace('%', '')))
                                 / float('0.' + (t5[1]).replace('%', ''))))
                if t5[0] == 'SApM':
                    if u5[1] > t5[1]:
                        fighter11.append('SApM' + '+' + str((float(u5[1]) - float(t5[1])) / float(u5[1])))
                        SApM.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('SApM' + '+' + str((float(t5[1]) - float(u5[1])) / float(t5[1])))
                if t5[0] == 'Str.Def':
                    if u5[1] > t5[1]:
                        fighter11.append('Str.Def' + '+' + str((float('0.' + u5[1].replace('%', '')) - float('0.' + t5[1].replace('%', '')))
                            / float('0.' + u5[1].replace('%', ''))))
                        Str_Def.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('Str.Def' + '+' + str((float('0.' + t5[1].replace('%', '')) - float('0.' + u5[1].replace('%', '')))
                            / float('0.' + t5[1].replace('%', ''))))
                if t5[0] == 'TDAvg.':
                    if u5[1] > t5[1]:
                        fighter11.append('TDAvg.' + '+' + str((float(u5[1]) - float(t5[1])) / float(u5[1])))
                        TD_Avg.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('TDAvg.' + '+' + str((float(t5[1]) - float(u5[1])) / float(t5[1])))
                if t5[0] == 'TDAcc.':
                    if u5[1] > t5[1]:
                        fighter11.append('TDAcc.' + '+' + str((float('0.' + u5[1].replace('%', '')) - float('0.' + t5[1].replace('%', '')))
                            / float('0.' + u5[1].replace('%', ''))))
                        TD_Acc.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('TDAcc.' + '+' + str((float('0.' + t5[1].replace('%', '')) - float('0.' + u5[1].replace('%', '')))
                            / float('0.' + t5[1].replace('%', ''))))
                if t5[0] == 'TDDef.':
                    if u5[1] > t5[1]:
                        fighter11.append('TDDef.' + '+' + str((float('0.' + u5[1].replace('%', '')) - float('0.' + t5[1].replace('%', '')))
                            / float('0.' + u5[1].replace('%', ''))))
                        TD_Def.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('TDDef.' + '+' + str((float('0.' + t5[1].replace('%', '')) - float('0.' + u5[1].replace('%', '')))
                            / float('0.' + t5[1].replace('%', ''))))
                if t5[0] == 'Sub.Avg.':
                    if u5[1] > t5[1]:
                        fighter11.append('Sub.Avg.' + '+' + str((float(u5[1]) - float(t5[1])) / float(u5[1])))
                        Sub_Avg.append(u5[1])
                    if t5[1] > u5[1]:
                        fighter22.append('Sub.Avg.' + '+' + str((float(t5[1]) - float(u5[1])) / float(t5[1])))
            list3.append('+'.join(fighter11))
            list4.append('+'.join(fighter22))
            
            would it be better to have two small for loops to format the lists and then run through the if statements or to leave it as is?
