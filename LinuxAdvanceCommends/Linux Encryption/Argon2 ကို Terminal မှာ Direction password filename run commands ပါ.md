

# Terminal directly commands ပါ

**Password file ကြိုတင်ဖန်တီးထားရန်လိုအပ်ပါသည်။**




```bash
cat password.txt | while read -r password; do
  echo -n "$password" | argon2 -id -p 2 -t 3 -m 16
done > hashed_passwords.txt

```

---
