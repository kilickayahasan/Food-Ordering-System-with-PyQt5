# Food-Ordering-System-with-PyQt5

This project is a user-friendly desktop application developed with **PyQt5**, designed to function as a client-side interface for a food ordering system. It enables users to easily browse through a restaurant's menu, add desired food items to their cart, and seamlessly place orders. The application aims to provide an intuitive and efficient way for customers to manage their food orders directly from their desktop, enhancing the overall ordering experience.

# Project Codes

import sys
from PyQt5.QtWidgets import QWidget,QApplication,QCheckBox,QLabel,QPushButton,QVBoxLayout,QRadioButton

class Pencere (QWidget) :

    def __init__(self):

        super().__init__()

        self.init_ui ()

    def init_ui(self) :

        self.yazi_alanı  =QLabel ("Hangi Yemekleri Seçtiniz : ")

        self.pizza = QCheckBox ("Pizza")
        self.hamburger = QCheckBox ("Hamburger")
        self.lahmacun = QCheckBox ("Lahmacun")
        self.icecek = QCheckBox ("İçecek")

        self.gönder = QPushButton ("Siparişi Gönder")
        self.temizle= QPushButton ("Temizle")

        self.paket = QRadioButton ("Paket Servis")
        self.gel = QRadioButton("Gel Al")

        v_box = QVBoxLayout ()

        v_box.addWidget(self.yazi_alanı)
        v_box.addWidget(self.pizza)
        v_box.addWidget(self.hamburger)
        v_box.addWidget(self.lahmacun)
        v_box.addWidget(self.icecek)
        v_box.addWidget(self.gönder)
        v_box.addWidget(self.temizle)
        v_box.addWidget(self.paket)
        v_box.addWidget(self.gel)

        self.setLayout(v_box)

        self.setWindowTitle ("Yemek Sipariş Sistemi")

        self.gönder.clicked.connect(self.siparis_olustur)

        self.temizle.clicked.connect (self.ekrani_temizle)

        self.show()

    def siparis_olustur (self):

        siparisler = []

        if self.pizza.isChecked() :

            siparisler.append("Pizza")

        if self.hamburger.isChecked() :

            siparisler.append("Hamburger")

        if self.lahmacun.isChecked() :

            siparisler.append("Lahmacun")


        if self.gönder.isChecked() :

            teslimat = "Paket Servis"

        elif self.gel.isChecked() :

            teslimat = "Gel Al"

        else :

            teslimat = "Teslimat türü belirtilmedi"


        if not siparisler :

            self.yazi_alanı.setText("Lütfen en az bir yemek seçiniz..")

        else :

            siparis_metni = "\n".join(siparisler)

            self.yazi_alanı.setText(f"Siparişiniz : {siparis_metni}\nTeslimat Türü : {teslimat}")



    def ekrani_temizle (self) :

        self.pizza.setChecked(False)
        self.hamburger.setChecked(False)
        self.lahmacun.setChecked(False)

        self.yazi_alanı.clear()


app =QApplication (sys.argv)

pencere = Pencere ()

sys.exit(app.exec_())


# Contact Me

hasankilickaya44@gmail.com

https://github.com/kilickayahasan/kilickayahasan
