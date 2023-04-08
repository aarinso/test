from PyQt5.QtCore import QtCore
from PyQt5.QtWidgets import QListWidget, QTextEdit, QLineEdit, QPushButton, QWidget, QApplication, QHBoxLayout
import json

app = QApplication([])
window = QWidget()

list_countries = QListWidget()
list_countries = QTextEdit()
name_countries = QLineEdit()
name_countries.setPlaceholderText('Введите страну')
button_add = QPushButton('Добавить страну')
button_del = QPushButton('Удалить страну')
button_edit = QPushButton('Изменить страну')

main_layout = QHBoxLayout()
second_layout = QVBoxLayout()
buttons_layout = QHBoxLayout()

buttons_layout.addWidget(button_add)
button_layout.addWidget(button_edit)
button_layout.addWidget(button_del)

second_layout.addWidget(text_countries)
second_layout.addWidget(main_countries)
second_layout.addWidget(button_del)

main_layout.addWidget(list_countries)
main_layout.addLayout(second_layout)

window.set_Layout(main_layout)

with open('countries.json', 'r', encoding='utf-8') as file:
    countries = jsom.load(file)
    for counry in countries:
        list_countries.addItem(country)


def add_country():
    countreies = {}
    with open('countries.json', 'r', enconding='utf-8') as file:
        counteies = json.load(file)
    country = name_countreis.text()
    countries[country] = ''
    list_countries.addItem(country)
    with open('countries.json', 'r', encoding='utf-8') as file:
        json.dump(countries, file)

def info_country():
    country = list_countries.selecteItems()[0].text()
    with open('contries.json', 'r', encoding='utf-8') as file:
        countries = json.load(file)
    text_countries.setText(countries[country])
    
def edit_country():
    if list_countries.selecteditems():
        country = list_countries.selectedItems()[0].text()
        text = text_countries.toPlainText()
        with open('countreies.json', 'r', encoding='uft-8') as file:
            coutries = json.load (file)
        countries[country] = text
        with open('countries.json', 'w', encoding='utf-8') as file:
            json.dump(countries, file)
        text_countries.clear()
    else:
        pass

def del_country():
    if  list_countrie.selectedItems():
        country = list_contries.selectedItems()[0].text()
        with open('countries.json', 'r', enconding='uft-8') as file:
            countries = json.load(file)
            del countries[country]
            text_countries.clear()
            list_countreis.clear()
            for country in countries:
                list_countries.addItem(country)
            with open ('countries.json', 'w', enconding='utf-8') as file:
                json.dump(countries, file)
    else:
        pass



button_add.clicked.conect(add_country)
button_edit.clicked.connect(edit_country)
button_del.clicked.connect(del_country)
list_countries.itemClicked.connect(info_country)




window.show()
app.exec()
