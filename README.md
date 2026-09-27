from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.label import Label
from kivy.uix.button import Button


class DemoLiveApp(App):

    def build(self):
        self.demo_balance = 10000.00
        self.live_balance = 0.00

        layout = BoxLayout(
            orientation="vertical",
            padding=30,
            spacing=20
        )

        self.title = Label(
            text="ABDULLAH TRADER",
            font_size=30
        )
        layout.add_widget(self.title)

        self.balance = Label(
            text=f"Demo Balance: ${self.demo_balance:,.2f}",
            font_size=24
        )
        layout.add_widget(self.balance)

        self.status = Label(
            text="DEMO MODE",
            font_size=20
        )
        layout.add_widget(self.status)

        button = Button(
            text="DEMO → SIMULATED LIVE",
            font_size=20
        )
        button.bind(on_press=self.convert)
        layout.add_widget(button)

        self.info = Label(
            text="Simulation only — not a real account",
            font_size=15
        )
        layout.add_widget(self.info)

        return layout

    def convert(self, instance):
        self.live_balance = self.demo_balance

        self.balance.text = (
            f"Simulated Live Balance: ${self.live_balance:,.2f}"
        )

        self.status.text = "SIMULATED LIVE MODE"

        self.info.text = (
            "SIMULATION ONLY — "
            "No real Quotex balance was changed"
        )


if __name__ == "__main__":
    DemoLiveApp().run()
