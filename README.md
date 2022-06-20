# webscrappingpropertylisting

from bs4 import BeautifulSoup
import requests

url= "https://www.pararius.com/apartments/amsterdam?ac=1"
page = requests.get(url)

soup = BeautifulSoup(page.content, 'html.parser')
lists = soup.find_all('section', class_="listing-search-item listing-search-item--list listing-search-item--for-rent")

for list in lists:
    title = list.find('a', class_="listing-search-item__link listing-search-item__link--title")
    location = list.find('div', class_="listing-search-item__location")
    price = list.find('div', class_="listing-search-item__price")
    area = list.find('li', class_="illustrated-features__item illustrated-features__item--surface-area")
    info = [title, location, price, area]
    print(info)

