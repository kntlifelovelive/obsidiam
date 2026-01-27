

---
# 1 
- sha256 check နည်း။ 

```bash

echo "709cdcfc6edda1f64e12e30a8e06b665e6e6da04dfbaf9bf25fbeb828f7de38e  tonarchy-2026.01.22-x86_64.iso" | sha256sum -c -


```



### 2
Sha256 hash ကို copy လုပ်ပါ ။ 

```bash 

sha256:709cdcfc6edda1f64e12e30a8e06b665e6e6da04dfbaf9bf25fbeb828f7de38e
```



# 3 
- Resualt sha256sum OK. 

```bash 

echo "709cdcfc6edda1f64e12e30a8e06b665e6e6da04dfbaf9bf25fbeb828f7de38e  tonarchy-2026.01.22-x86_64.iso" | sha256sum -c -
tonarchy-2026.01.22-x86_64.iso: OK

```



```bash 

sha256sum -c --ignore-missing sha256sum.txt  

sha256sum.txt ထဲက code format ============

`709cdcfc6edda1f64e12e30a8e06b665e6e6da04dfbaf9bf25fbeb828f7de38e tonarchy-2026.01.22-x86_64.iso`

```

### 4 

- sha256sum txt code format 
`709cdcfc6edda1f64e12e30a8e06b665e6e6da04dfbaf9bf25fbeb828f7de38e tonarchy-2026.01.22-x86_64.iso`

```bash 
709cdcfc6edda1f64e12e30a8e06b665e6e6da04dfbaf9bf25fbeb828f7de38e tonarchy-2026.01.22-x86_64.iso

```