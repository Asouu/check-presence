# check-presence*



from kivy.uix.textinput import TextInput



from kivy.uix.gridlayout import GridLayout



from kivy.uix.button import Button



from kivy.uix.label import Label



from kivy.app import App



class MApp(App):
    def __init__(self):
        super(MApp, self).__init__()
        self.label = Label(text = '')

    @property
    def name(self):
        return self._name

    def build(self):
        layout = GridLayout(cols=3, rows=2)
        self.name = TextInput(text='enter employer name here')
        absent = Button(text='absent', on_press=self.absent)
        present = Button(text='present', on_press=self.present)
        self.label= Label (text = "")
        layout.add_widget(self.name)
        layout.add_widget(absent)
        layout.add_widget(present)
        layout.add_widget(self.label)
        return layout

    def absent (self, obj):
        print("  " + self.name.text + " is absent")
        self.label = Label (text ='is absent')


    def present (self, obj):
        print("  " + self.name.text + " is present")
        self.label = Label (text ='is present')

    @name.setter
    def name(self, value):
        self._name = value


MApp ().run()
