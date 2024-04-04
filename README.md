# instainfobot
Tool for insta 
GNU nano 7.2                       
#!/bin/python
import os,sys,requests,telebot
from subprocess import run
os.system("clear")
logo="""\a\a
⠀⠀⠀⠀⠀⢀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣠⣴⣷⣶⣶⣤⣄⠀⠀⠀
⠀⠀⢀⣶⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⣄⠀
⠀⢠⣿⣿⣿⣿⣿⡿⠟⠛⠛⠛⠛⠛⠛⠛⠛⠛⠛⠛⠻⢿⣿⣿⣿⣿⣿⣿⣆
⠀⣼⣿⣿⣿⡿⠋⢀⣠⣴⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣤⡀⠈⢻⣿⣯⣿⣿⣻
⠡⣿⣿⣿⣿⠁⢠⣿⣿⣿⣿⣿⣿⡿⣿⢿⣿⣿⣟⠉⠙⣿⡆⠀⢿⣿⣟⣿⣽
⡁⣿⣿⣿⡿⠀⣸⣿⣿⣿⡿⠋⠀⣀⣠⣀⠈⠙⢿⣶⣾⣿⡷⠀⢺⣿⣿⡷⠊
⡀⣿⣿⣿⡟⠀⢸⣿⣿⡿⠀⢠⣿⣿⡿⣿⣿⣆⠀⢻⣿⣽⣟⠀⢼⣿⣿⡽⠀
⡐⣿⣿⢿⣯⠀⢸⣿⣟⣧⠀⢿⣿⣳⣿⣟⣷⣿⠀⢸⣿⣯⡷⠀⢸⣿⣟⡿⠀
⢧⣿⣻⡿⣷⠀⢸⣿⡽⣿⡄⠈⠿⣿⣾⣽⠾⠃⢀⣿⣿⡽⣟⠀⢺⣿⣟⡿⠀
⣯⣷⢿⣻⣿⠀⢸⡿⣽⣳⢿⣶⣄⣀⣀⣀⣠⣴⡿⣟⣷⣿⡯⠀⣽⣿⣻⣟⠀
⣷⣟⣯⢷⣻⡆⠈⢿⣳⢯⣛⡾⡽⢯⣟⡿⣯⢿⣽⣻⣽⡾⠃⢀⣿⣿⣽⡯⣄
⢿⣟⡞⣯⢳⣛⢦⡀⠉⠙⠛⠚⠛⠛⠚⠛⠛⠛⠛⠋⠉⢀⣠⣾⣿⣻⣾⢿⣟
⠈⢿⣞⡱⢳⡌⢧⡙⡛⠖⡶⠲⠖⣆⢖⡲⢶⢶⡶⣾⣾⢿⣟⣿⣽⡿⣽⣿⠃
⠀⠈⠻⢷⣧⣘⣢⠡⠙⢌⠰⢉⠚⠤⢋⠼⣩⢞⣹⢳⣯⢿⣞⣿⣾⡿⠟⠁⠀                                                                                                                          ⠀⠀⠀⠀⠉⠓⠛⠛⠿⠛⠟⠻⠛⠟⠻⠻⠝⠯⠛⠯⠛⢟⠛⣓⠋⠁InstaInfo Bot 1.0

    A Telegram bot made for insta osint\n
"""

run(["lolcat"],input=logo, text=True)
print("\33[0;1mAuthor \33[32;1m: \33[31;1mbad__army_yt")
try:
  import tok
except:
  tok=input("\33[0mBot_Token : ")
  with open("tok.py","w") as xx:
    xx.write('tok='+'"'+tok+'"')
    os.system("mv tok.py $PATH")
from tok import tok
print("\33[32;1mBot started")
bot=telebot.TeleBot(tok)                                                                                                                               @bot.message_handler(commands=['start'])

def message(message):
  bot.send_message(message.chat.id,'<strong>  Bot Coded BY:- @bad__army_yt \n Type your track insta username</strong>',parse_mode='html')
@bot.message_handler(func=lambda message:True)
def sta(message):
  user=message.text
  head={'x-ig-app-id':'936619743392459'}
  url=f'https://www.instagram.com/api/v1/users/web_profile_info/?username={user}'
  req=requests.get(url,headers=head).json()['data']['user']
  i=req['id']
  p=req['profile_pic_url']
  fo=req['edge_followed_by']['count']
  fw=req['edge_follow']['count']
  b=req['biography']
  m=req['edge_owner_to_timeline_media']['count']
  fid=req['fbid']
  ib=req['is_business_account']
  date = requests.get(f"https://o7aa.pythonanywhere.com/?id={i}").json()['date']
  bot.send_photo(message.chat.id,p,f'<strong>- Followers : {fo}\n- Following : {fw}\n- ID :<code> {i}</code>\n- Date : {date}\n- Posts : {m}\n- FB-ID >
bot.polling(True)
