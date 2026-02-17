# Занятие 5

Просмотр текущей таблицы

```bash
ip neigh
arp -n
```

Состояния записи

* **reachable**
* **stale**
* **delay**
* **failed**

```bash
cat /proc/sys/net/ipv4/neigh/default/base_reachable_time
cat /proc/sys/net/ipv4/neigh/default/gc_stale_time
cat /proc/sys/net/ipv4/neigh/default/delay_first_probe_time
```

Захватываем ARP пакеты
```bash
sudo tcpdump -n -e arp
```

`-n Don't convert addresses (i.e., host addresses, port numbers, etc.) to names. `

`-e Print the link-level header on each dump line.`

Удаляем запись:
```bash
sudo ip neigh del <IP> dev <iface>
```

Добавляем static запись:
```bash
sudo ip neigh add <IP> lladdr <MAC> dev <iface> nud permanent
```

Сброс ARP таблицы:
```bash
sudo ip neigh flush all
```

Сброс интерфейса:
```bash
sudo ip link set <iface> down
sudo ip link set <iface> up
```

```bash
sudo tcpdump -n -e -vvv arp
```

Захват ARP (hex вывод):
```bash
sudo tcpdump -n -e -vvv -XX arp
```

Идентифицируйте поля:
* Hardware type
* Protocol type
* Opcode
* Sender MAC/IP
* Target MAC/IP

Сравниваем с таблицей ядра:
```bash
cat /proc/net/arp
```
