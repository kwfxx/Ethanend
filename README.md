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
hash=['59133419746d7da1e3e3bb1382299c823bd79a66fca3b45bf07d351c5df5680a','f2fa637d0b3e518870979685ec43903ee9735ea40a2a1d9f17537735e27c9758','47921ca1c3f6bda073c4b3422d3c610a8f573ebce0af797f2cd69550a19547b0','1c1be9d6a46d4ef12f4f1ffa0274efc513c88d30acb214a650ea584c0dad2f28','eeaed30664a309dc7b92c7a3d61b2b9fd6036dbb17984117b48543bb139c6aa5','fb5f29a42f393fb5e8025cf4c387bc736d1efa0dc132ea1a317d367d3d1faf91','2f466c97e83dd5611f9f8828a7e54c82dc02e15663828e05c244a6effcbec26a','4dbdbfab22dcd9eafc9e764536dd0bf07d8e2e369b5d6622b849d4ca16ca789b','0f9541560ac1a2bb629ee473c175a222818f306524f4ef8b4e4b2751a46eb021','57d32ba92e8903b5eb344a55fe9d1287d82f7ec286353674a30c7b3cfcd5ceda','7df5c0932fe9564504455d1ed7e52da785e85ba1436cde2b7cdff384da4a5faa','fecf08bf0358220bd8d3628afca146ed5c73ee97c903915dae2475742f8cf0f8','39475abdd6d7700bb30aa7d0711c3dc96feba087bd4a1d6934f57dd1234426b7','9e259ee9ab063f208a494e03aa8d23a343541165ded9b92dcb655c3e71127627','283d2a06aa26383c7021abe060cf5ec9907d7b0a1b6c5cac43c6aa96c83872e2','2f6c72b6e343b52fd0150a61a4c8cbaad234e5fe1aa644572491433682ccfa7b','25f5d963fd5a761230fe16a809746fcdeee6785a5729ff84bba6a742a21e79f2','5f854214482fa6d7013bf3b0b3c6d3abbcdf32f883d1d866437903586f630de3','55ce387a49d064b3da5671d77a3a8895db8108b0ad347e834aa571f2fc417b40','621d87219abc72dc85bf4a395a530e30f2a20afb9a4fec45501a014e38482339','6d04401681161cdf7ce10cef675c86e44084b65de5db0d4afb664e9ce523135b','9b8f00e0e36b78821568aa4159f548333f00ce0f5c6ae618b7a87e0417ed49c6','5492156e8956344a4cfd3ec430368d2d85a4c8fca36ce8a4ca7e2f30f6eb25b0']
if h in hash:
    print('good / هاتفك مصرح للدخول ')
    pass
else :
	while True:
	   print('your code is /', h)
	   print()
	   print('للتفعيل راسل المطور وادفع حق التحديث 1 usdt او 2k رشق وبعدها ارسله الكود يفعل لك ملاحضة لا تدور مجاني . ماراح ارد عليك')
	   time.sleep(90)
     
