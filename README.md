# change-iface-name
## Как да сменим името на интерфейса от ens3а0 на eth0

##### Досадното сменяне на интерфейса трови живота на много хора, в новите версии на Debian, Ubuntu и другите дебиан базирани се наблюдава масово мрежовият интерфейс да има име от рода на ens3а0  и сходни. Тук описвам кратка процедура за смяна на името на интерфейса. Започваме.

*Отиваме в конфигурацията на grub*
> nano /etc/default/grub
> 
*там намираме следния ред*
> GRUB_CMDLINE_LINUX=""

*променяме го да стане*
> GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"
> 

*след което конфигурираме наново*

> grub-mkconfig -o /boot/grub/grub.cfg
> 
*после се отива и си сменяме имената на интерфеисите в interfaces*

```
nano /etc/network/interfaces
auto ens33
iface ens33 inet dhcp
```

*на* 

```
auto eth0
iface eth0 inet dhcp
auto ens33
iface ens33 inet dhcp
``` 
*на* 
``` 
auto eth0
iface eth0 inet dhcp
```
----
и накрая да не забравим reboot
