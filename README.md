import subprocess
import hashlib
import time
def run(cmd):
    try:
        out = subprocess.check_output(cmd, shell=True, stderr=subprocess.DEVNULL)
        return out.decode().strip()
    except Exception:
        return ""

android_id = run("settings get secure android_id")
serial = run("getprop ro.serialno") or run("getprop ro.boot.serialno") or run("getprop ro.hardware")
brand = run("getprop ro.product.brand")
model = run("getprop ro.product.model")
mac = run("cat /sys/class/net/wlan0/address 2>/dev/null")
values = [v for v in [android_id, serial, brand, model, mac] if v]
concat = "|".join(values)

SALT = "سِرّ_خاص_قوي_غير_مُشارَك"

full = SALT + "|" + concat
h = hashlib.sha256(full.encode()).hexdigest()
hash=['59133419746d7da1e3e3bb1382299c823bd79a66fca3b45bf07d351c5df5680a','f2fa637d0b3e518870979685ec43903ee9735ea40a2a1d9f17537735e27c9758','47921ca1c3f6bda073c4b3422d3c610a8f573ebce0af797f2cd69550a19547b0','1c1be9d6a46d4ef12f4f1ffa0274efc513c88d30acb214a650ea584c0dad2f28','eeaed30664a309dc7b92c7a3d61b2b9fd6036dbb17984117b48543bb139c6aa5','fb5f29a42f393fb5e8025cf4c387bc736d1efa0dc132ea1a317d367d3d1faf91','2f466c97e83dd5611f9f8828a7e54c82dc02e15663828e05c244a6effcbec26a']
if h in hash:
    print('good / هاتفك مصرح للدخول ')
    pass
else :
	while True:
	   print('your code is /', h)
	   print()
	   print('للتفعيل راسل المطور وادفع حق التحديث 1 usdt او 2k رشق وبعدها ارسله الكود يفعل لك ملاحضة لا تدور مجاني . ماراح ارد عليك')
	   time.sleep(90)
     
