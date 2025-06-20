
## 🚗 MotorCompany SQL Database System

This project provides a fully designed **relational SQL database** to model the backend of a **motor and real estate management system**. It simulates how a motor company may manage its car brands (makes), models, users, brokers, logins, and related personal data in a well-normalized and relational manner.

---

### 🏗️ Database Name

**`motorcompany`**

---

### 🧱 Tables Overview

| Table Name             | Purpose                                                                 |
| ---------------------- | ----------------------------------------------------------------------- |
| `Make_table`           | Stores car manufacturer (make) details like ID, name, status, added by  |
| `model`                | Stores vehicle models, references `Make_table`                          |
| `personal_information` | Stores detailed personal profiles of users, brokers, and agents         |
| `login_user`           | Stores login credentials and user type for system authentication        |
| `broker`               | Stores additional professional info for brokers linked to personal data |

---

### 📄 Table Descriptions

#### 1. `Make_table`

* Contains unique car make records.
* Fields include: `make_id`, `make_desc`, `make_status`, `added_on`, `added_by`.
* Constraints:

  * Primary Key: `make_id`
  * Unique Keys: `make_desc`, `added_on`

#### 2. `model`

* Contains vehicle model details.
* Fields: `model_id`, `model_desc`, `model_status`, `m_added_on`, `m_added_by`
* Foreign Keys:

  * `model_desc` → `make_desc` of `Make_table`
  * `m_added_on` → `added_on` of `Make_table`

#### 3. `personal_information`

* Stores users' profile data including contact, education, and demographics.
* Covers users of type: `user`, `broker`, `agent`.
* Includes city, state, and country constraints to ensure valid locality data.
* Constraints:

  * Primary Key: `user_id`
  * Check constraints on user type, marital status, city, state, and country
  * Unique: `added_on`, `added_by`

#### 4. `login_user`

* Stores login credentials mapped to users.
* Fields: `login_id`, `u_password`, `l_user_id`, `lead_id`, `l_user_type`, `l_status`, `l_added_on`, `l_added_by`
* Foreign Key: `l_user_id` → `user_id` of `personal_information`

#### 5. `broker`

* Contains extra details related to brokers such as their organization, contact info, and status.
* Fields: `broker_id`, `broker_name`, `broker_org_name`, `contact_info`, `b_status`, `b_added_on`, `b_added_by`
* Foreign Key: `broker_id` → `user_id` of `personal_information`

---

### 🧪 Features & Integrity

* **Referential Integrity** using foreign keys ensures accurate relationships.
* **Data Validation** through `CHECK` constraints (e.g., allowed cities/states/user types).
* **Sample Data**: All tables are populated with realistic example entries (30+ records each).
* **User Types**: Clearly separated logic for different actors: users, brokers, agents.
* **Extensible**: Can be easily scaled to support vehicle sales, broker listings, etc.

---

### 🔧 Use Cases

This schema is ideal for:

* Learning database design & normalization.
* Prototyping vehicle dealership or real estate management systems.
* Teaching referential integrity, constraints, and relational data modeling.

---

