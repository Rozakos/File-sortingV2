import re
import os


serial_list = os.listdir('C:\LC_CPE_DATA\LC_CPE_CNTRL_DataLog_FT05')
for i in serial_list:
    try:
        os.chdir('C:\LC_CPE_DATA\LC_CPE_CNTRL_DataLog_FT05\\' + i)
        with open("C:\LC_CPE_DATA\LC_CPE_CNTRL_DataLog_FT05\\" + i + '\\' + i + '_DATA.txt'" "r"") as f:
            lines = open("C:\LC_CPE_DATA\LC_CPE_CNTRL_DataLog_FT05\\" + i + '\\' + i + '_DATA.txt').read()
            first_line = f.readline()
            Voltage_Data = re.findall(r'24 ; 1\d\w\d\s;\s\d\d.\d\d\d?\s;\s\s;\s\w\w\w\w\s;\s\d\d,\d\d\s;\s\d\d,\d\d\s;', lines)
            Date = re.findall(r'\d\d:\d\d?\d\d?',lines)
            Ycode = re.findall(r'\w\d\d-\d\d\w/\d\d.\w\d',lines)
            print(Ycode[0] + ' ; ' + i + ' ; ' + ' ; ' + Voltage_Data[0] + ' ; ' + Date[0])
    except IndexError:
        pass


