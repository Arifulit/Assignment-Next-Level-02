
# PostgreSQL সম্পর্কিত প্রশ্ন ও উত্তর 

## ১. PostgreSQL কী?
PostgreSQL হলো একটি ওপেন-সোর্স রিলেশনাল ডাটাবেস ম্যানেজমেন্ট সিস্টেম (RDBMS)। এটি ডাটার নিরাপদ সংরক্ষণ ও পরিচালনার জন্য ব্যবহৃত হয়। PostgreSQL উচ্চ ক্ষমতার SQL কমান্ড সাপোর্ট করে এবং ডাটা কনসিস্টেন্সি বজায় রাখে।  
**উদাহরণ:** অনলাইন স্টোরের পণ্য এবং অর্ডার সম্পর্কিত ডাটা PostgreSQL এ সংরক্ষণ করা যায়।

---

## ২. PostgreSQL-এ Database Schema-এর উদ্দেশ্য কী?
Schema হলো ডাটাবেসের মধ্যে টেবিল, ভিউ, ফাংশন ইত্যাদি ডাটাবেস অবজেক্টের সংগঠন। এটি ডাটাবেসকে বিভিন্ন লজিক্যাল অংশে ভাগ করে এবং একই ডাটাবেসে আলাদা আলাদা স্কিমা থেকে কাজ চালানো যায়।  
**উদাহরণ:** `sales` ও `hr` নামে দুইটি স্কিমা তৈরি করে সংশ্লিষ্ট ডাটা আলাদাভাবে রাখা যায়।

---

## ৩. PostgreSQL-এ Primary Key এবং Foreign Key কী?
- **Primary Key:** একটি টেবিলের ইউনিক কলাম যা প্রতিটি রেকর্ডকে অনন্য করে চিহ্নিত করে।  
- **Foreign Key:** একটি টেবিলের কলাম যা অন্য টেবিলের Primary Key কে রেফার করে, টেবিলগুলোর মধ্যে সম্পর্ক তৈরি করে।  
**উদাহরণ:**

```sql
CREATE TABLE departments (
    department_id SERIAL PRIMARY KEY,
    department_name VARCHAR(50)
);

CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```

---

## ৪. SELECT স্টেটমেন্টে WHERE ক্লজের উদ্দেশ্য কী?
`WHERE` ক্লজ ব্যবহার করে নির্দিষ্ট শর্ত অনুযায়ী ডাটা ফিল্টার করা হয়, অর্থাৎ প্রয়োজনীয় রেকর্ডগুলো সিলেক্ট করা হয়।  
**উদাহরণ:** বেতন ৫০০০০ এর বেশি যেসব কর্মচারী আছেন, তাদের নাম দেখতে:

```sql
SELECT name FROM employees WHERE salary > 50000;
```

---

## ৫. PostgreSQL-এ LIMIT এবং OFFSET ক্লজ কী জন্য ব্যবহার করা হয়?
- **LIMIT:** কতগুলো রেকর্ড প্রদর্শন করতে হবে।  
- **OFFSET:** কতগুলো রেকর্ড বাদ দিতে হবে।  
দুটি একসাথে Pagination বা ডাটার পেজ বাই পেজ দেখানোর জন্য ব্যবহৃত হয়।  
**উদাহরণ:** ১১ থেকে ২০ পর্যন্ত রেকর্ড দেখতে:

```sql
SELECT * FROM employees LIMIT 10 OFFSET 10;
```

---

