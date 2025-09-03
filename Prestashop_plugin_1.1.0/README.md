
# Модуль платежів EcommerceConnect для PrestaShop

## Опис

Модуль дозволяє приймати платежі через платіжну систему UPC eCommerceConnect із підтримкою стандартних платежів та режиму пре-авторизації (холд коштів із подальшим списанням у бек-офісі).

---

## Вимоги

- **PrestaShop**: >= 1.7.x (рекомендовано 8.x)
- **PHP**: >= 7.4 (підтримуються також 8.0, 8.1)
- **cURL**: увімкнено
- **OpenSSL**: увімкнено

---

## Установка

1. Скопіюйте папку `ecconnect` у директорію `/modules` вашого магазину PrestaShop.
2. Увійдіть до **Адмін-панелі PrestaShop** → **Модулі** → **Менеджер модулів** → **Встановити модуль**.
3. Активуйте модуль **EcommerceConnect Payment Gateway**.

---

## Налаштування

1. Перейдіть у **Модулі** → **EcommerceConnect Payment Gateway**.
2. Введіть:
   - **Merchant ID** (отриманий від банку)
   - **Terminal ID**
   - **Gateway URL**
   - **Публічний ключ (сертифікат)** платіжної системи
   - (Опційно) **Тестовий режим**
3. Збережіть налаштування.
---

## Використання

### 1. **Стандартна оплата**

- Клієнт здійснює оплату, після успішної транзакції замовлення автоматично отримує статус **Оплачено**.

### 2. **Оплата з пре-авторизацією**

- Клієнт підтверджує оплату, кошти блокуються на рахунку покупця.
- Замовлення отримує статус **На утриманні (Pre-authorized)**.
- Адміністратор може у бек-офісі PrestaShop на сторінці замовлення натиснути **Оплатити** (Capture), щоб списати кошти.
- Після успішного списання замовлення змінює статус на **Оплачено**.

---

## Webhook

URL для отримання повідомлень від платіжного сервісу:
```
https://yourshop.com/index.php?fc=module&module=ecconnect&controller=callback
```

Webhook автоматично:
- Перевіряє підпис відповіді
- Оновлює статус замовлення
- Зберігає технічну інформацію про транзакцію

---

## Інструкція англійською

# EcommerceConnect Payment Module for PrestaShop

## Description

This module enables payments via UPC eCommerceConnect payment gateway, supporting both standard payments and pre-authorization mode (funds hold with subsequent capture in the back office).

---

## Requirements

- **PrestaShop**: >= 1.7.x (recommended 8.x)
- **PHP**: >= 7.4 (supports 8.0, 8.1)
- **cURL**: enabled
- **OpenSSL**: enabled

---

## Installation

1. Upload the `ecconnect` folder to `/modules` in your PrestaShop installation.
2. Go to **PrestaShop Admin Panel** → **Modules** → **Module Manager** → **Upload a module**.
3. Activate **EcommerceConnect Payment Gateway**.

---

## Configuration

1. Go to **Modules** → **EcommerceConnect Payment Gateway**.
2. Fill in:
   - **Merchant ID** (provided by your bank)
   - **Terminal ID**
   - **Gateway URL**
   - **Public Key (certificate)** from the payment provider
   - (Optional) **Test Mode**
3. Save settings.
---

## Usage

### 1. **Standard Payment**

- Customer pays, and upon successful payment, the order is automatically marked as **Paid**.

### 2. **Pre-authorization Payment**

- Customer authorizes payment, funds are held on their account.
- Order is marked as **On hold (Pre-authorized)**.
- Administrator can capture the funds via the **Capture** button on the order page in PrestaShop.
- After successful capture, the order status changes to **Paid**.

---

## Webhook

Webhook URL for receiving payment notifications:
```
https://yourshop.com/index.php?fc=module&module=ecconnect&controller=callback
```

The webhook automatically:
- Validates response signature
- Updates order status
- Stores technical transaction details
