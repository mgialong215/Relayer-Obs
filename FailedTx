import requests
import threading

URL = "https://api-osmosis.cosmostation.io/v1/account/new_txs/$walletAddr"
Addr = "$walletAddr"
PARAMS = {'limit': 50,'from': 0}

listFailHeight = []

def addListHeight():
  r = requests.get(url=URL, params=PARAMS)
  datas = r.json()
  for data in datas:
    if(data["data"]["code"] != 0):
      if(data["data"]["height"] not in listFailHeight):
        listFailHeight.append(data["data"]["height"])
        print ("missed tx:" + data["data"]["height"])
      else:
        print ("")

def setInterval(func,time):
    e = threading.Event()
    while not e.wait(time):
        func()

setInterval(addListHeight,10)
