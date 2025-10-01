
---

### Ghostty  Ubuntu 

###  ၁။ `Rust` install 

Ghostty ကို Rust နဲ့ build လုပ်ရတယ်။

```bash
sudo apt update
sudo apt install curl git -y
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```

---

###  ၂။ Ghostty Repo Clone 

```bash
git clone https://github.com/ghostty-org/ghostty
cd ghostty
```

---

###  ၃။ Required dependencies install

```bash
sudo apt install libwayland-dev libxkbcommon-dev \
libfontconfig1-dev libfreetype6-dev \
libxcb-render0-dev libxcb-shape0-dev libxcb-xfixes0-dev -y
```

---

###  ၄။ Build လုပ်ပါ

```bash
cargo build --release
```

---

###  ၅။ Binary ကို Copy ပြုလုပ်ပါ

```bash
mkdir -p ~/.local/bin
cp target/release/ghostty ~/.local/bin/
```

---

### ၆။ PATH ထဲမှာ ပါလား စစ်ပါ

```bash
echo $PATH
```

မရှိရင် `.bashrc` (သို့) `.zshrc` ထဲမှာ ထည့်ပါ

```bash
export PATH="$HOME/.local/bin:$PATH"
source ~/.bashrc
```

---

###  ၇။ Ghostty  Start 

```bash
ghostty
```

---

##  မရတာတွေ ဖြစ်နေရင်?

==> `ghostty: command not found` ဆိုရင်  
 PATH မှာ မထည့်ရသေးတာ

 ==> `--install` error ဆိုရင်  
 `ghostty` CLI မှာ `--install` ဆိုတာ မပါဘူး။ တကယ် run ချင်တာက `ghostty` ဆိုပြီးပဲ ရိုက်ရပါတယ်။


---

