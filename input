import math

# Asal sayıları seç
p = 13
q = 17

# n hesapla
n = p * q

# φ(n) hesapla
phi = (p - 1) * (q - 1)

# Genel anahtar (e) seç
e = 37

# Özel anahtarı (d) hesapla (e * d ≡ 1 mod φ(n))
def mod_inverse(a, m):
    m0, x0, x1 = m, 0, 1
    while a > 1:
        q = a // m
        m, a = a % m, m
        x0, x1 = x1 - q * x0, x0
    return x1 + m0 if x1 < 0 else x1

d = mod_inverse(e, phi)

# Genel ve özel anahtarları yazdır
print(f'Genel Anahtar (e, n): ({e}, {n})')
print(f'Özel Anahtar (d, n): ({d}, {n})')

# Şifrelenecek metni seç
plain_text = 42

# Mesajı şifrele (C = M^e mod n)
encrypted_text = pow(plain_text, e, n)
print(f'Mesajın Kendisi: {plain_text}')
print(f'Şifrelenmiş Mesaj: {encrypted_text}')

# Şifreli mesajı çöz (M = C^d mod n)
decrypted_text = pow(encrypted_text, d, n)

print(f'Çözülmüş Mesaj: {decrypted_text}')
