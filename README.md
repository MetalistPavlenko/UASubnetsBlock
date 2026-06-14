# UASubnetsBlock

**Заблоковані підмережі в Україні**

---

- **IPv4:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/IPv4.txt)

- **IPv6:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/IPv6.txt)

- **Range (IPv4):**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/ranges.txt)

- **Subnets (IPv4 + IPv6):**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/subnets.txt)

---

- **Routes (IPv4) для RouterOS:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/routes4.rsc)

- **Routes (IPv6) для RouterOS:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/routes6.rsc)

- **Routes (IPv4 + IPv6) для RouterOS:**
  [Переглянути список](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/routes.rsc)

---

- **GeoIP для sing-box:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/geoip.srs)

- **GeoIP (IPv4) для sing-box:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/geoip-v4.srs)

- **GeoIP (IPv6) для sing-box:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/geoip-v6.srs)

---

- **GeoIP для xray-core / v2ray-core / mihomo:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/geoip.dat)

- **GeoIP (IPv4) для xray-core / v2ray-core / mihomo:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/geoip-v4.dat)

- **GeoIP (IPv6) для xray-core / v2ray-core / mihomo:**
  [Завантажити базу](https://raw.githubusercontent.com/MetalistPavlenko/UASubnetsBlock/main/geoip-v6.dat)

---

<details>
<summary style="font-size: 1.1em;"><strong>Застосування в RouterOS:</strong></summary>

#### **Імпортування:**

> **1. Потрібно замінити `gateway` у файлі `routes.rsc` на ваш шлюз**

> **2. Завантажуємо файл `routes.rsc` у прошивку**

> **3. Створюємо нову таблицю маршрутизації:**
>> ```shell
>> /routing/table/add fib name=UASubnetsBlock
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
>> /ip/route/remove [find routing-table=UASubnetsBlock]
>> ```
>> ```shell
>> /ipv6/route/remove [find routing-table=UASubnetsBlock]
>> ```

> **3. Видаляємо таблицю маршрутизації:**
>> ```shell
>> /routing/table/remove [find name=UASubnetsBlock]
>> ```
</details>