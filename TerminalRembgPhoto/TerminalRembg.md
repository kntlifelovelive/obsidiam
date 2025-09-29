

---
### Arch Linux  `rembg` Install


```bash
sudo pacman -S python python-pip

pip install rembg

```

### Python Virtual Environment

```bash

python -m venv ~/venvs/rembg
source ~/venvs/rembg/bin/activate

pip install rembg

disactivate

```

### Run Photo Background Remove 

- Run bellow command your terminal 

```bash

rembg i ~/Pictures/path/your.png ~/Pictures/your_trans.png

```

