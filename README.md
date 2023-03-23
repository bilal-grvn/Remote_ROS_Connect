# Remote_ROS_Connect

<h4 align="left">
Yazar : Bilal GÜREVİN👋👋
</h4>

<p align="center">
  <img width="400" height="200" src="img/pc-jetson.png?raw=true">
</p>

### -- Bu repo aynı ağa bağlı olan, farklı bir `UBUNTU` bilgisayarındaki `ROS` ekosistemine bağlanmak için gerekli bilgileri içermektedir.

### -- Bu sayede `ROS` bilgisayarının kurulu olduğu `PC`'ye `terminal` ekranı vasıtasıyla uzaktan erişim sağlanmakta ve `ROS` tarafından yapılan `topic`'ler dinlenebilmektedir.

### -- Örneğin bir dizüstü PC den Jetson Nano mikrobilgisayarına bağlanacağımızı düşünelim. Her ikisinde de ubuntu işletim sistemi bulunmaktadır.

### -- Aşağıdaki satırı yazarak IP adresimizi öğrenebiliriz.

```sh
ifconfig
```
### -- Burada PC için IP adresi `192.168.1.102`, jetson Nano için IP adresi `192.168.1.113` olarak ele alınmıştır.

### -- Hem PC hem de Jetson Nano terminal ekranında aşağıdaki satırı yazalım.
```sh
sudo gedit ~/.bashrc
```
### -- çıkan dosya içerisine aşağıdaki satırları ekleyelim. Buradaki `11311` sayısı default olarak `ROS` portunu ifade etmektedir.

## 🚀 JETSON NANO tarafı için (MASTER - yayın yapan taraf)
```sh
export ROS_MASTER_URI=http://192.168.1.113:11311/
export ROS_HOSTNAME=192.168.1.113
export ROS_IP=192.168.1.113
```

## 🚀 PC tarafı için (SLAVE - dinleyici taraf)
```sh
export ROS_MASTER_URI=http://192.168.1.113:11311/
export ROS_HOSTNAME=192.168.1.102
export ROS_IP=192.168.1.102
```
### -- Kayıt edip çıktıktan sonra derleme işlemi yapması için yeni bir terminal açmamız ya da aşağıdaki satırı yazmamız gerekmektedir.

```sh
source ~/.bashrc
```
### -- Bu işlemlerden sonra ortak ağ içerisinde iken Jetson Nano'dan yapılan yayınlar PC tarafından dinlebilecektir. PC tarafında `RVİZ` programını açarak yapılan yayınları görselleştirebiliriz.

### -- PC tarafında terminal ekranına aşağıdaki satırı yazarsak Jetson Nano'ya ssh bağlantısı yapabiliriz. Bu sayede PC'den Jetson Nano'ya giriş yaparak `roscore` u aktif edebiliriz. `roscore` aktif olduktan sonra PC'den terminal ekranına `rostopic` yazarak Jetson Nano'dan yapılan yayınları dinleyebiliriz. `bilal` burada Jetson Nano'daki kullanıcı ismidir.

```sh
sudo ssh bilal@192.168.1.113
```

# 🚀 NOT:
## -- bazı durumlarda güvenklik duvarı bağlantıya izin vermeyebilir. Bunun için bağlanılacak olan tarafta aşağıdaki işlemler kullanılabilir.

güvenlik duvarı durumunu sorgulamak için
```sh
sudo ufw status verbase
```

uzak bağlantıya izin vermek için
```sh
sudo ufw allow ssh
``` 

güvenlik duvarını kapatmak için
```sh
sudo ufw disable
```

güvenlik duvarını açmak için
```sh
sudo ufw enable
```

***************************************************************