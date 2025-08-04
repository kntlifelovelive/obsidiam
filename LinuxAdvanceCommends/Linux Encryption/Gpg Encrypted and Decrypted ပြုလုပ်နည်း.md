
# Encrypt လုပ်တဲ့ Command (Encrypting a file)

```bash
gpg --batch --yes --passphrase-file < password hashfile == hash_passwdlove.txt> --symmetric --digest-algo SHA512 --cipher-algo AES256 --output < user-choice ouptfile-name လိုချင်သောနာမည်ထည့်ရန် ==lover.gpg > <user-data-original-zipfile == ထည့်ရန် == master.zip>

```

**1.Commands ရှင်းလင်းချက်**

- `--batch`: Batch mode 
- `--yes`: အကြောင်းအရာ တစ်ခုခု မေးလာရင် အလိုအလျောက် "yes" ပေးပါမယ်။
- `--passphrase-file hash_passwdlove.txt`: ဖိုင် hash_passwdlove.txt ထဲက passphrase ကို encryption လုပ်ရာမှာ သုံးပါမယ်။
- `--symmetric`: Symmetric encryption ကို အသုံးပြုပြီး file ကို encrypt လုပ်ပါမယ်။
- `--digest-algo SHA512`: SHA512 hashing algorithm ကို အသုံးပြုပြီး encryption လုပ်ပါမယ်။
- `--cipher-algo AES256`: AES256 cipher algorithm ကို encryption အတွက် အသုံးပြုပါမယ်။
- `--output lover.gpg`: အရင်ဆုံး encrypt လုပ်ပြီး ဖိုင်ကို lover.gpg အမည်နဲ့ output ထုတ်ပါမယ်။


---
# Decrypt လုပ်တဲ့ Command (Decrypting a file)

```bash
gpg --batch --yes --passphrase-file hash_passwdlove.txt --output <lover_decrypted.zip> --decrypt <lover.gpg>

```


- `--batch`: Batch mode အတွက် ပါ၊  မေးမြန်းခြင်း မဖြစ်ပါ။
- `--yes`: ဘာများကို "yes" ဖြည့်စွက်မလဲ။
- `--passphrase-file hash_passwdlove.txt`: hash_passwdlove.txt ဖိုင်ထဲက passphrase ကို decrypt လုပ်ရာမှာ သုံးပါမယ်။
- `--output lover_decrypted.zip`: decrypted ဖိုင်ကို lover_decrypted.zip အမည်နဲ့ output ထုတ်ပါမယ်။
- `--decrypt lover.gpg`: lover.gpg ဖိုင်ကို decrypt လုပ်ပါမယ်။

### Summary:
- Encrypt ဖိုင်ကို --output lover.gpg နဲ့ ဖိုင် lover.gpg အဖြစ် output ထုတ်ပါတယ်။
- Decrypt ဖိုင်ကို --output lover_decrypted.zip နဲ့ lover.gpg ဖိုင်ကို lover_decrypted.zip အဖြစ် output ထုတ်ပါမယ်။
- Gpg Encrypted သည် Security high-level cli ဖြစ်သည်။
  