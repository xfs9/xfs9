import requests, time

print("""

                 ,  ,
              #▄▓██████▀
            "▀███████████▄L
           ▄R████████████▄▄
            ▄▀█████████▓▀▀N
             ' ▀█▀███▀█ ▀
                ' ▀█▌"
                   ▐█
                   ██
                   ██
    ""▀▀▀██▄▄   ▄▄▄██▄a▄▄   ,▄▄██▀▀""
           "▀██▄⌠▀▀▀▀▀'¡▄██▀"
               ▀██▄  ▄██▀`
                  ████"
               ▄▄█▌▀╙██▄▄
          ██▄▄██▀█    █▀███▀█▌

     [ Made By GIVT . ]
     [ + ] Telegram : givtt
     [ + ] Instagram : we62
     [ ! ] You are not entitled to sell the Tool [ ! ]
""")
time.sleep(2)

class LordGivt:
    def __init__(self, username):
        self.username = username
        print("[+] Getting Info ..")
        self.run()

    def run(self):
        r = requests.get(f"https://api.givtt.com/api/ig/info_username/{self.username}", allow_redirects=False, timeout=50)

        if "error" in r.text and r.json()["error"] is True:
            if r.json()["message"] == "==":
                return self.run()
            input(f"[X] Error -> {r.json()['message']}")
            exit()

        else:
            print(f"[ Get Info For @{self.username} ] ..\n\n")

            result = r.json()["result"]
            print("[-] Username:", result["username"])
            print("[-] Username ID:", result["username_id"])
            print("[-] Name:", result["name"])
            print("[-] Bio:", result["bio"])
            print("[-] External URL:", result["external_url"])
            print("[-] Is Business account:", "Yes" if result["business_account"] else "No")
            print("[-] Is Verified account:", "Yes" if result["verified_account"] else "No")
            print("[-] Is Private account:", "Yes" if result["private_account"] else "No")
            print("[-] Followers:", result["followers"])
            print("[-] Following:", result["following"])
            print("[-] Account created before 30 days?:", "Yes" if result['account_created_before_30d'] else "No")
            print("[-] Has threads:", "Yes" if result["has_threads"] is True else "No")
            print("[-] Has videos:", result.get("has_videos", "None"))
            print("[-] Media count:", result["media_count"])
            print("[-] Total IGTV videos:", result["total_igtv_videos"])
            print("[-] Is in Canada:", result.get("is_in_canada", False))
            print("[-] Is memorialized Account:", result.get("is_memorialized", False))
            print("[-] Is new account:", "Yes" if result["is_new_account"] is True else "No")
            print("[-] Public email:", result.get("public_email", "None"))
            print("[-] Public phone number:", result.get("public_phone_number", "None"))
            print("[-] User have another account:", "Yes" if result["user_have_another_account"] is True else "No")
            print("[-] Account region:", result.get("account_region", ""))
            print("[-] Create time:", result.get("create_time", ""))
            print("[-] Last time edit avatar:", result["last_time_edit_avatar"])
            print("[-] Profile pic:", result["profile_pic"])

            input("\n[ + ] Done Sir ..")

user = input("[?] Please Enter Username: ")
LordGivt(user)
