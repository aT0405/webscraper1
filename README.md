# webscraper1
import urllib.request as req
url="https://webscraper.io/test-sites/e-commerce/allinone"
request=req.Request(url,headers={
    "User-Agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.128 Safari/537.36"
})
with req.urlopen(request)as response:
    data=response.read().decode("utf-8")
import bs4
root=bs4.BeautifulSoup(data,"html.parser")
titles=root.find_all("div",class_="caption")
for title in titles:
    if title.h4!=None:
        print(title.a.string)
        print(title.h4.string)
        print(title.p.string)
        print("")
