import random

# İki büyük asal sayı seçimi
def generate_prime(bits):
    while True:
        num = random.getrandbits(bits)
        if is_prime(num):
            return num

# Bir sayının asal olup olmadığını kontrol etme
def is_prime(n, k=5):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0:
        return False

    # Miller-Rabin testi kullanarak asal olup olmadığını kontrol etme
    r, s = 0, n - 1
    while s % 2 == 0:
        r += 1
        s //= 2

    for _ in range(k):
        a = random.randint(2, n - 2)
        x = pow(a, s, n)
        if x == 1 or x == n - 1:
            continue
        for _ in range(r - 1):
            x = pow(x, 2, n)
            if x == n - 1:
                break
        else:
            return False
    return True

# İki büyük asal sayıyı seçme
bits = 512
p = generate_prime(bits)
q = generate_prime(bits)

# n hesaplama
n = p * q

# Euler'in φ(n) fonksiyonunu hesaplama
phi = (p - 1) * (q - 1)

# Genel anahtar üretme
def generate_public_key(phi):
    e = 65537  # Eğer başka bir değer kullanmak isterseniz, burayı değiştirebilirsiniz.
    return e, n

# Özel anahtar üretme
def generate_private_key(e, phi):
    d = mod_inverse(e, phi)
    return d, n

# İki sayının modüler tersini hesaplama (genel anahtar oluştururken gerekli)
def mod_inverse(a, m):
    m0, x0, x1 = m, 0, 1
    while a > 1:
        q = a // m
        m, a = a % m, m
        x0, x1 = x1 - q * x0, x0
    return x1 + m0 if x1 < 0 else x1

# Genel ve özel anahtarları üretme
public_key = generate_public_key(phi)
private_key = generate_private_key(public_key[0], phi)

print("Genel Anahtar (e, n):", public_key)
print("Özel Anahtar (d, n):", private_key)
