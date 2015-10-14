# HiDe-repo
Socially Relevant Projects
AutoHiDe.py

from Adafruit_CharLCD import Adafruit_CharLCD
from subprocess import *
from time import sleep, strftime
from datetime import datetime

lcd = Adafruit_CharLCD()

cmd = "ip addr show eth0 | grep inet | awk '{print $2}' | cut -d/ -f1"

lcd.begin(16, 1)


def run_cmd(cmd):
    p = Popen(cmd, shell=True, stdout=PIPE)
    output = p.communicate()[0]
    return output

while 1:
    #lcd.clear()
    lcd.noBlink()
    #ipaddr = run_cmd(cmd)
    #lcd.message(datetime.now().strftime('%b %d  %H:%M:%S\n'))
    #lcd.message('IP %s' % (ipaddr))
    #sleep(2)
    lcd.clear()
    lcd.begin(16,2)
    lcd.setCursor(5,0)
    lcd.message('WELCOME!')
    lcd.setCursor(0,1)
    lcd.message('Cafeteria, KPark')
    sleep(4)
    lcd.home()
    lcd.clear()
    toknum = raw_input("")
    lcd.message(toknum)
    sleep(1)
    lcd.clear()
    lcd.home()
    lcd.message('Order No.: %s' % (toknum))
    lcd.blink()
    sleep(4)

