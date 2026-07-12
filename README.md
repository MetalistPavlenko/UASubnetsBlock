# UASubnetsBlock

**Заблоковані підмережі в Україні**

---

- **IPv4:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/txt/ipv4/list.txt)

- **IPv6:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/txt/ipv6/list.txt)

- **Ranges (IPv4):**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/txt/ranges/list.txt)

- **Subnets (IPv4 + IPv6):**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/txt/all/list.txt)

---

- **Routes (IPv4) для RouterOS:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/rsc/ipv4/routes.rsc)

- **Routes (IPv6) для RouterOS:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/rsc/ipv6/routes.rsc)

- **Routes (IPv4 + IPv6) для RouterOS:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/rsc/all/routes.rsc)

---

- **GeoIP для sing-box:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/srs/all/geoip.srs)

- **GeoIP (IPv4) для sing-box:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/srs/ipv4/geoip.srs)

- **GeoIP (IPv6) для sing-box:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/srs/ipv6/geoip.srs)

---

- **GeoIP для xray-core / v2ray-core / mihomo:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/dat/all/geoip.dat)

- **GeoIP (IPv4) для xray-core / v2ray-core / mihomo:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/dat/ipv4/geoip.dat)

- **GeoIP (IPv6) для xray-core / v2ray-core / mihomo:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/dat/ipv6/geoip.dat)

---

<details>
<summary style="font-size: 1.1em;"><strong>Застосування в RouterOS:</strong></summary>

#### **Імпортування:**

> **1. Потрібно замінити `gateway` у файлі `routes.rsc` на ваш шлюз**

> **2. Завантажуємо файл `routes.rsc` у прошивку**

> **3. Створюємо нову таблицю маршрутизації:**
>> ```shell
>> /routing table add fib name=UASubnetsBlock
>> ```

> **4. Імпортуємо маршрути:**
>> ```shell
>> /import file-name=routes.rsc
>> ```

> **5. Створюємо правило таблиці маршрутизації:**
>> ```shell
>> /routing rule add action=lookup table=UASubnetsBlock
>> ```

#### **Видалення:**

> **1. Видаляємо правило таблиці маршрутизації:**
>> ```shell
>> /routing rule remove [find table=UASubnetsBlock]
>> ```

> **2. Видаляємо маршрути:**
>> ```shell
>> /ip route remove [find routing-table=UASubnetsBlock]
>> ```
>> ```shell
>> /ipv6 route remove [find routing-table=UASubnetsBlock]
>> ```

> **3. Видаляємо таблицю маршрутизації:**
>> ```shell
>> /routing table remove [find name=UASubnetsBlock]
>> ```
</details>