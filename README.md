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
