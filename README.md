# Информационная система для управления складскими запасами на предприятии

## 1. Краткое описание проекта

### 1.1. ФИО разработчиков:
Айтибаева Нуриза Кубанычбековна


### 1.2. Группа:
Д-Э306

### 1.3. Тема проекта:
Проектирование и разработка информационной системы для управления складскими запасами на предприятии.

### 1.4. Цель проекта:
Создать автоматизированную систему для учета, контроля и оптимизации складских запасов предприятия.

### 1.5. Задачи проекта:
1. Провести анализ предметной области "Управление складом".
2. Разработать модели бизнес-процессов (IDEF0, BPMN, DFD).
3. Спроектировать структуру базы данных (ER-диаграмма).
4. Реализовать backend-часть системы на [Python/Django/Node.js/др.].
5. Разработать frontend-интерфейс на [React/Vue/HTML+CSS].
6. Протестировать систему и подготовить документацию.

### 1.6. Аннотация:
Система предназначена для автоматизации учета товаров на складе, отслеживания перемещений, управления заказами и формирования отчетов. Позволяет снизить издержки, избежать пересортицы и оптимизировать логистику.

---

## 2. Документация
### 2.1 Подробное описание проекта
#### 1. Введение
Предприятию необходимо автоматизировать учёт товарных запасов на складе. В настоящее время учёт ведётся вручную, что приводит к ошибкам, затрудняет контроль остатков и замедляет процессы приёма/отпуска товаров.
#### 2. Целевая аудитория
Кладовщики
Менеджеры по закупкам
Логисты
Руководители отдела снабжения
#### 3. Функциональные требования
##### 3.1. Управление товарами:
Добавление, редактирование, удаление товаров
Учет категорий, поставщиков, единиц измерения
Установка минимального остатка (точка заказа)
##### 3.2. Складские операции:
Приём товара на склад
Отпуск товара со склада
Внутренние перемещения
Инвентаризация
##### 3.3. Отчетность:
Остатки на складе в реальном времени
Движение товаров за период
Товары с истекшим сроком годности
Отчет по поставщикам
#### 4. Нефункциональные требования
Веб-интерфейс
Многопользовательский доступ с ролями
Резервное копирование БД
Простота использования
#### 5. Технологический стек
Бэкенд: Python + FastAPI (или Django)
Фронтенд: React + TypeScript (или Vue.js)
БД: PostgreSQL
Контейнеризация: Docker

### 2.2. Ментальная карта (с комментариями)

<img width="716" height="701" alt="mind-map" src="https://github.com/user-attachments/assets/5a456db3-fef4-4aa5-a239-f0de9b17068a" />

Представленная ментальная карта демонстрирует полноценный и логичный каркас для проектирования системы управления складом. Её ключевые достоинства:

Полнота охвата: Карта структурирует систему по всем критическим направлениям — от фундаментальных справочников («Товары») до операционных процессов («Прием», «Отпуск»), управления доступом («Роли») и аналитики («Отчеты»). Ничего лишнего, ничего не упущено.

Ясная логика потоков: Четко прослеживается жизненный цикл товара — он появляется в системе через справочник, поступает на склад (Прием), перемещается внутри (Перемещение), покидает его (Отпуск) и периодически пересчитывается (Инвентаризация). Все операции фиксируются (Учет) и доступны для анализа.

Баланс между операциями и управлением: Карта удачно разделяет ежедневную работу (блок «Складские операции») и инструменты для ее контроля и оптимизации (блоки «Учет» и «Отчеты»). Особенно важен последний блок, так как он трансформирует сырые данные в основу для решений (Прогноз покупок).

Учет человеческого фактора: Выделение блока «Пользователи и роли» — признак продуманной архитектуры. Это прямо указывает на необходимость разграничения прав (кладовщик не должен видеть финансовую аналитику, а менеджер — не может проводить инвентаризацию), что критично для безопасности и порядка.

Главный вывод: Эта карта — не просто список функций, а отражение бизнес-логики будущей системы. Она показывает, что система заточена под реальные процессы: товар движется, его движение учитывается, а на основе учета строятся отчеты для принятия решений. Это прочный фундамент для следующего этапа — детального описания каждого элемента (например, какие конкретно данные содержит карточка поставщика или по какому алгоритму строится прогноз покупок).

### 2.3. Модель в нотации IDEF0 (с комментариями)

<img width="662" height="341" alt="A-0-Context drawio" src="https://github.com/user-attachments/assets/1cfc8ab2-a9bb-4fd4-9c6d-8ee6acdc7384" />

Данная диаграмма определяет границы и ключевые взаимодействия системы управления складскими запасами предприятия с внешней средой.
Главные элементы:
Центральный процесс: «Управление складскими запасами предприятия» — ядро системы, преобразующее входящие потоки в результаты.
Входы:
Заказы клиентов — первичный запрос, запускающий процесс.
Информация об остатках и потребностях — данные для планирования и контроля.
Выход: Отгруженные товары клиентам — конечный материальный результат работы системы.
Управление:
Политики управления запасами — регламенты и правила работы.
Бюджетные ограничения (С1, С2) — финансовые рамки деятельности.
Механизмы (ресурсы):
Система управления складом (WMS) — программное обеспечение для автоматизации.
Персонал склада — человеческий ресурс для выполнения операций.
Диаграмма наглядно показывает, что система функционирует под влиянием стратегических правил и бюджета, использует автоматизацию и труд персонала для выполнения клиентских заказов на основе данных об остатках.

#### 2.3.1. Декомопзиция первого уровня (с комментариями)
<img width="581" height="309" alt="A0-Main-Functions drawio (2)" src="https://github.com/user-attachments/assets/984d4293-def5-4452-afeb-6f8215f52f5a" />

Данная диаграмма представляет декомпозицию основного процесса управления складскими запасами на четыре ключевых взаимосвязанных блока, образующих полный операционный цикл. В центре системы находится Планирование закупок, которое на основе политик управления запасами и бюджетных ограничений определяет потребность в товарах. Результатом планирования становится реализация процесса Приемка товаров, где поступающая продукция фиксируется и размещается на складе. Далее вступает в действие Учет и контроль, обеспечивающий постоянную актуальность данных о местонахождении, количестве и состоянии товарных остатков. Завершающим звеном является Отгрузка товаров, в рамках которой товары подготавливаются и передаются клиентам согласно их заказам.

Все эти процессы осуществляются с использованием ключевых механизмов: ERP-система служит для интеграции финансовых и учетных данных, Система WMS — для оперативного управления складскими операциями, Персонал склада выполняет физические действия, а Оборудование склада обеспечивает техническую поддержку. Таким образом, диаграмма наглядно демонстрирует, как стратегические установки и планы преобразуются в логическую цепочку практических действий по движению товара от поставщика к потребителю.

#### 2.3.2. Диаграмма второго уровня (с комментариями)
![Uploading d2.drawio.png…]()


### 2.4 Диаграмма потоков данных (DFD)
<img width="711" height="551" alt="dfd drawio" src="https://github.com/user-attachments/assets/b3dc3f65-6198-42a8-9b36-b79d64d10527" />

Данная DFD-диаграмма уровня 0 наглядно отображает ключевые информационные потоки в системе управления складскими запасами. В центре модели находятся четыре основных процесса, образующих логический цикл работы: «Планирование закупок», «Приемка товаров», «Учет и контроль» и «Отгрузка товаров». Диаграмма демонстрирует, что инициатором работы системы является клиент, который отправляет заказ и получает подтверждение отгрузки. Ключевым элементом является центральное хранилище «Остатки», с которым взаимодействуют все процессы: приемка увеличивает остатки, отгрузка уменьшает их, а учет проводит корректировки. Менеджер взаимодействует с системой через запросы и получает данные для принятия решений, в то время как поставщик выступает источником товаров и получателем планов закупок. Диаграмма подчеркивает замкнутый характер информационного контура, где данные о каждом действии фиксируются и влияют на последующие операции, обеспечивая целостность и актуальность данных в системе.

### 2.5 Модель в нотации BPMN (с комментариями)
<img width="811" height="293" alt="bpnm drawio" src="https://github.com/user-attachments/assets/7b518db4-a931-48a9-b52f-22cb23ad9097" />

Данная BPMN-диаграмма наглядно описывает процесс обработки запроса клиента на товар в системе управления складскими запасами. Процесс начинается с получения запроса от клиента, после чего система автоматически проверяет наличие запрашиваемого товара на складе. Ключевым решающим элементом является шлюз, который определяет дальнейший путь процесса в зависимости от результата проверки. Если товар присутствует в достаточном количестве, он резервируется за клиентом, и система отправляет подтверждение бронирования, успешно завершая процесс. В случае отсутствия товара клиенту предлагаются альтернативные варианты, такие как аналогичный товар или информация о предполагаемых сроках поступления, после чего процесс также завершается. Диаграмма демонстрирует четкую логику принятия решений и два возможных сценария работы системы, обеспечивая прозрачность и эффективность обработки клиентских запросов.

### 2.6. Модели в нотации UML.
<img width="451" height="381" alt="uml1 drawio" src="https://github.com/user-attachments/assets/f08d8368-7b2f-4dd8-874a-5bd0b71ecc48" />
<img width="601" height="309" alt="uml2 drawio" src="https://github.com/user-attachments/assets/e0b8ced4-ddcf-407a-ad5d-a40246dd8832" />

Первая диаграмма представляет собой UML-диаграмму классов, которая отображает статическую структуру данных информационной системы управления складом. Диаграмма включает пять ключевых классов: Client (Клиент), Order (Заказ), Product (Товар), OrderItem (Позиция заказа) и Category (Категория). Каждый класс содержит атрибуты, описывающие его свойства, такие как идентификаторы, названия, цены и количества, а также методы, определяющие возможные действия, например, размещение заказа, расчет общей суммы или проверка наличия товара. Эта диаграмма служит основой для проектирования базы данных и объектно-ориентированной реализации системы, четко определяя сущности и их взаимосвязи.

Вторая диаграмма является UML-диаграммой вариантов использования, которая иллюстрирует взаимодействие внешнего актера "Сотрудник" с системой. Диаграмма выделяет пять основных сценариев использования: сборка заказа, приемка поставки, списание товара в брак, проверка наличия товара на складе и общее управление складскими операциями. Эта диаграмма фокусируется на функциональных возможностях системы с точки зрения конечного пользователя, показывая, какие конкретные действия сотрудник может выполнять в рамках системы для эффективного управления складскими процессами. Обе диаграммы взаимно дополняют друг друга, предоставляя как структурный, так и функциональный взгляд на проектируемую информационную систему.

### 2.7 ER-диаграмма

<img width="382" height="603" alt="er drawio" src="https://github.com/user-attachments/assets/17b8a33c-66c8-4515-ad20-1384797af58e" />

Данная ER-диаграмма представляет структуру базы данных информационной системы управления складскими запасами предприятия. Диаграмма включает пять основных сущностей: CLIENT (Клиент), ORDER (Заказ), ORDER_ITEM (Позиция заказа), PRODUCT (Товар) и CATEGORY (Категория). Для каждой сущности определены атрибуты с выделением первичных ключей (PK), обеспечивающих уникальность записей, и внешних ключей (FK), устанавливающих связи между таблицами. Диаграмма наглядно отображает отношения между сущностями: клиенты формируют заказы, которые состоят из нескольких позиций, каждая позиция ссылается на конкретный товар, а товары группируются по категориям. Эта модель обеспечивает целостность данных, минимизирует избыточность информации и служит основой для разработки нормализованной реляционной базы данных системы.

## 3. База данных

CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    role VARCHAR(20) NOT NULL CHECK (role IN ('admin', 'manager', 'warehouse_worker', 'client')),
    full_name VARCHAR(100),
    phone VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    is_active BOOLEAN DEFAULT TRUE
);

CREATE TABLE clients (
    client_id SERIAL PRIMARY KEY,
    user_id INTEGER UNIQUE NOT NULL REFERENCES users(user_id) ON DELETE CASCADE,
    company_name VARCHAR(100),
    address TEXT,
    tax_id VARCHAR(50),
    discount_rate DECIMAL(5,2) DEFAULT 0.00,
    credit_limit DECIMAL(10,2) DEFAULT 0.00,
    notes TEXT
);

CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    user_id INTEGER UNIQUE NOT NULL REFERENCES users(user_id) ON DELETE CASCADE,
    position VARCHAR(50) NOT NULL,
    department VARCHAR(50),
    hire_date DATE NOT NULL,
    salary DECIMAL(10,2),
    supervisor_id INTEGER REFERENCES employees(employee_id)
);

CREATE TABLE categories (
    category_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    parent_category_id INTEGER REFERENCES categories(category_id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE suppliers (
    supplier_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    contact_person VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(20),
    address TEXT,
    tax_id VARCHAR(50),
    rating DECIMAL(3,2) DEFAULT 5.00 CHECK (rating >= 0 AND rating <= 5),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE products (
    product_id SERIAL PRIMARY KEY,
    sku VARCHAR(50) UNIQUE NOT NULL,
    name VARCHAR(200) NOT NULL,
    description TEXT,
    category_id INTEGER REFERENCES categories(category_id) ON DELETE SET NULL,
    supplier_id INTEGER REFERENCES suppliers(supplier_id),
    unit_price DECIMAL(10,2) NOT NULL CHECK (unit_price >= 0),
    cost_price DECIMAL(10,2) NOT NULL CHECK (cost_price >= 0),
    barcode VARCHAR(100),
    weight DECIMAL(10,3),
    dimensions VARCHAR(50),
    min_stock_level INTEGER DEFAULT 10,
    max_stock_level INTEGER DEFAULT 100,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_updated TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE warehouses (
    warehouse_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    location VARCHAR(200),
    capacity INTEGER,
    manager_id INTEGER REFERENCES employees(employee_id),
    is_active BOOLEAN DEFAULT TRUE
);

CREATE TABLE storage_locations (
    location_id SERIAL PRIMARY KEY,
    warehouse_id INTEGER NOT NULL REFERENCES warehouses(warehouse_id) ON DELETE CASCADE,
    location_code VARCHAR(50) NOT NULL,
    aisle VARCHAR(10),
    shelf VARCHAR(10),
    bin VARCHAR(10),
    max_capacity INTEGER,
    current_usage INTEGER DEFAULT 0,
    UNIQUE(warehouse_id, location_code)
);

CREATE TABLE product_inventory (
    inventory_id SERIAL PRIMARY KEY,
    product_id INTEGER NOT NULL REFERENCES products(product_id) ON DELETE CASCADE,
    location_id INTEGER REFERENCES storage_locations(location_id),
    warehouse_id INTEGER NOT NULL REFERENCES warehouses(warehouse_id),
    quantity INTEGER NOT NULL DEFAULT 0 CHECK (quantity >= 0),
    batch_number VARCHAR(50),
    expiration_date DATE,
    last_counted DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(product_id, location_id, batch_number)
);

CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    order_number VARCHAR(50) UNIQUE NOT NULL,
    client_id INTEGER NOT NULL REFERENCES clients(client_id) ON DELETE CASCADE,
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(20) NOT NULL DEFAULT 'new' 
        CHECK (status IN ('new', 'processing', 'packing', 'shipped', 'delivered', 'cancelled')),
    total_amount DECIMAL(10,2) NOT NULL DEFAULT 0,
    discount_amount DECIMAL(10,2) DEFAULT 0,
    final_amount DECIMAL(10,2) NOT NULL DEFAULT 0,
    payment_status VARCHAR(20) DEFAULT 'pending' 
        CHECK (payment_status IN ('pending', 'partial', 'paid', 'refunded')),
    shipping_address TEXT,
    notes TEXT,
    employee_id INTEGER REFERENCES employees(employee_id),
    completed_at TIMESTAMP
);

CREATE TABLE order_items (
    order_item_id SERIAL PRIMARY KEY,
    order_id INTEGER NOT NULL REFERENCES orders(order_id) ON DELETE CASCADE,
    product_id INTEGER NOT NULL REFERENCES products(product_id),
    quantity INTEGER NOT NULL CHECK (quantity > 0),
    unit_price DECIMAL(10,2) NOT NULL CHECK (unit_price >= 0),
    discount_percent DECIMAL(5,2) DEFAULT 0,
    total_price DECIMAL(10,2) GENERATED ALWAYS AS (quantity * unit_price * (1 - discount_percent/100)) STORED,
    status VARCHAR(20) DEFAULT 'reserved' 
        CHECK (status IN ('reserved', 'picked', 'packed', 'shipped'))
);

CREATE TABLE purchase_orders (
    purchase_order_id SERIAL PRIMARY KEY,
    po_number VARCHAR(50) UNIQUE NOT NULL,
    supplier_id INTEGER NOT NULL REFERENCES suppliers(supplier_id),
    order_date DATE NOT NULL DEFAULT CURRENT_DATE,
    expected_delivery_date DATE,
    status VARCHAR(20) NOT NULL DEFAULT 'draft' 
        CHECK (status IN ('draft', 'ordered', 'partial', 'received', 'cancelled')),
    total_amount DECIMAL(10,2) NOT NULL DEFAULT 0,
    notes TEXT,
    created_by INTEGER REFERENCES employees(employee_id)
);

CREATE TABLE purchase_order_items (
    po_item_id SERIAL PRIMARY KEY,
    purchase_order_id INTEGER NOT NULL REFERENCES purchase_orders(purchase_order_id) ON DELETE CASCADE,
    product_id INTEGER NOT NULL REFERENCES products(product_id),
    quantity INTEGER NOT NULL CHECK (quantity > 0),
    unit_cost DECIMAL(10,2) NOT NULL CHECK (unit_cost >= 0),
    received_quantity INTEGER DEFAULT 0,
    status VARCHAR(20) DEFAULT 'ordered'
);

CREATE TABLE receipts (
    receipt_id SERIAL PRIMARY KEY,
    receipt_number VARCHAR(50) UNIQUE NOT NULL,
    purchase_order_id INTEGER REFERENCES purchase_orders(purchase_order_id),
    supplier_id INTEGER NOT NULL REFERENCES suppliers(supplier_id),
    receipt_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    received_by INTEGER REFERENCES employees(employee_id),
    warehouse_id INTEGER REFERENCES warehouses(warehouse_id),
    status VARCHAR(20) DEFAULT 'received' 
        CHECK (status IN ('partial', 'received', 'verified', 'problem')),
    notes TEXT
);

CREATE TABLE receipt_items (
    receipt_item_id SERIAL PRIMARY KEY,
    receipt_id INTEGER NOT NULL REFERENCES receipts(receipt_id) ON DELETE CASCADE,
    product_id INTEGER NOT NULL REFERENCES products(product_id),
    po_item_id INTEGER REFERENCES purchase_order_items(po_item_id),
    quantity_received INTEGER NOT NULL CHECK (quantity_received > 0),
    quantity_accepted INTEGER,
    quantity_rejected INTEGER DEFAULT 0,
    rejection_reason TEXT,
    unit_cost DECIMAL(10,2),
    expiration_date DATE,
    batch_number VARCHAR(50),
    location_id INTEGER REFERENCES storage_locations(location_id)
);

CREATE TABLE shipments (
    shipment_id SERIAL PRIMARY KEY,
    shipment_number VARCHAR(50) UNIQUE NOT NULL,
    order_id INTEGER NOT NULL REFERENCES orders(order_id),
    shipment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    shipped_by INTEGER REFERENCES employees(employee_id),
    carrier VARCHAR(100),
    tracking_number VARCHAR(100),
    status VARCHAR(20) DEFAULT 'preparing' 
        CHECK (status IN ('preparing', 'ready', 'shipped', 'delivered', 'problem')),
    shipping_cost DECIMAL(10,2),
    notes TEXT
);

CREATE TABLE inventories (
    inventory_id SERIAL PRIMARY KEY,
    inventory_number VARCHAR(50) UNIQUE NOT NULL,
    warehouse_id INTEGER NOT NULL REFERENCES warehouses(warehouse_id),
    start_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    end_date TIMESTAMP,
    conducted_by INTEGER REFERENCES employees(employee_id),
    status VARCHAR(20) DEFAULT 'in_progress' 
        CHECK (status IN ('planned', 'in_progress', 'completed', 'cancelled')),
    total_items INTEGER DEFAULT 0,
    discrepancies INTEGER DEFAULT 0,
    notes TEXT
);

CREATE TABLE inventory_items (
    inventory_item_id SERIAL PRIMARY KEY,
    inventory_id INTEGER NOT NULL REFERENCES inventories(inventory_id) ON DELETE CASCADE,
    product_id INTEGER NOT NULL REFERENCES products(product_id),
    location_id INTEGER REFERENCES storage_locations(location_id),
    system_quantity INTEGER NOT NULL,
    counted_quantity INTEGER NOT NULL,
    difference INTEGER GENERATED ALWAYS AS (counted_quantity - system_quantity) STORED,
    notes TEXT,
    UNIQUE(inventory_id, product_id, location_id)
);

CREATE TABLE write_offs (
    write_off_id SERIAL PRIMARY KEY,
    write_off_number VARCHAR(50) UNIQUE NOT NULL,
    product_id INTEGER NOT NULL REFERENCES products(product_id),
    warehouse_id INTEGER NOT NULL REFERENCES warehouses(warehouse_id),
    location_id INTEGER REFERENCES storage_locations(location_id),
    quantity INTEGER NOT NULL CHECK (quantity > 0),
    reason VARCHAR(100) NOT NULL 
        CHECK (reason IN ('expired', 'damaged', 'lost', 'theft', 'quality_issue', 'other')),
    write_off_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    approved_by INTEGER REFERENCES employees(employee_id),
    cost_loss DECIMAL(10,2),
    notes TEXT
);

CREATE TABLE transfers (
    transfer_id SERIAL PRIMARY KEY,
    transfer_number VARCHAR(50) UNIQUE NOT NULL,
    product_id INTEGER NOT NULL REFERENCES products(product_id),
    from_location_id INTEGER NOT NULL REFERENCES storage_locations(location_id),
    to_location_id INTEGER NOT NULL REFERENCES storage_locations(location_id),
    quantity INTEGER NOT NULL CHECK (quantity > 0),
    transfer_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    transferred_by INTEGER REFERENCES employees(employee_id),
    status VARCHAR(20) DEFAULT 'requested' 
        CHECK (status IN ('requested', 'approved', 'in_transit', 'completed', 'cancelled')),
    notes TEXT
);

CREATE TABLE system_settings (
    setting_id SERIAL PRIMARY KEY,
    setting_key VARCHAR(100) UNIQUE NOT NULL,
    setting_value TEXT,
    description TEXT,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_products_category ON products(category_id);
CREATE INDEX idx_products_supplier ON products(supplier_id);
CREATE INDEX idx_products_sku ON products(sku);
CREATE INDEX idx_products_name ON products(name);
CREATE INDEX idx_inventory_product ON product_inventory(product_id);
CREATE INDEX idx_inventory_location ON product_inventory(location_id);
CREATE INDEX idx_inventory_warehouse ON product_inventory(warehouse_id);
CREATE INDEX idx_orders_client ON orders(client_id);
CREATE INDEX idx_orders_status ON orders(status);
CREATE INDEX idx_orders_date ON orders(order_date);
CREATE INDEX idx_orders_number ON orders(order_number);
CREATE INDEX idx_order_items_order ON order_items(order_id);
CREATE INDEX idx_order_items_product ON order_items(product_id);
CREATE INDEX idx_po_supplier ON purchase_orders(supplier_id);
CREATE INDEX idx_po_status ON purchase_orders(status);
CREATE INDEX idx_receipts_po ON receipts(purchase_order_id);
CREATE INDEX idx_receipts_supplier ON receipts(supplier_id);
CREATE INDEX idx_shipments_order ON shipments(order_id);
CREATE INDEX idx_shipments_status ON shipments(status);

CREATE OR REPLACE FUNCTION update_product_timestamp()
RETURNS TRIGGER AS $$
BEGIN
    NEW.last_updated = CURRENT_TIMESTAMP;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trg_update_product_timestamp
BEFORE UPDATE ON products
FOR EACH ROW
EXECUTE FUNCTION update_product_timestamp();

CREATE OR REPLACE FUNCTION update_order_total()
RETURNS TRIGGER AS $$
BEGIN
    UPDATE orders o
    SET total_amount = COALESCE((
        SELECT SUM(total_price)
        FROM order_items oi
        WHERE oi.order_id = o.order_id
    ), 0),
    final_amount = COALESCE((
        SELECT SUM(total_price)
        FROM order_items oi
        WHERE oi.order_id = o.order_id
    ), 0) - COALESCE(o.discount_amount, 0)
    WHERE o.order_id = NEW.order_id OR o.order_id = OLD.order_id;
    
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trg_update_order_total_insert
AFTER INSERT ON order_items
FOR EACH ROW
EXECUTE FUNCTION update_order_total();

CREATE TRIGGER trg_update_order_total_update
AFTER UPDATE ON order_items
FOR EACH ROW
EXECUTE FUNCTION update_order_total();

CREATE TRIGGER trg_update_order_total_delete
AFTER DELETE ON order_items
FOR EACH ROW
EXECUTE FUNCTION update_order_total();

CREATE OR REPLACE FUNCTION update_inventory_on_receipt()
RETURNS TRIGGER AS $$
BEGIN
    UPDATE product_inventory pi
    SET quantity = pi.quantity + NEW.quantity_accepted
    WHERE pi.product_id = NEW.product_id 
      AND pi.location_id = NEW.location_id
      AND (pi.batch_number = NEW.batch_number OR (pi.batch_number IS NULL AND NEW.batch_number IS NULL));
    
    IF NOT FOUND THEN
        INSERT INTO product_inventory (
            product_id, location_id, warehouse_id, 
            quantity, batch_number, expiration_date
        )
        SELECT 
            NEW.product_id,
            NEW.location_id,
            w.warehouse_id,
            NEW.quantity_accepted,
            NEW.batch_number,
            NEW.expiration_date
        FROM storage_locations sl
        JOIN warehouses w ON sl.warehouse_id = w.warehouse_id
        WHERE sl.location_id = NEW.location_id;
    END IF;
    
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trg_update_inventory_on_receipt
AFTER INSERT OR UPDATE ON receipt_items
FOR EACH ROW
WHEN (NEW.quantity_accepted IS NOT NULL)
EXECUTE FUNCTION update_inventory_on_receipt();

CREATE OR REPLACE FUNCTION reserve_stock_on_order()
RETURNS TRIGGER AS $$
DECLARE
    available_quantity INTEGER;
BEGIN
    SELECT COALESCE(SUM(quantity), 0) INTO available_quantity
    FROM product_inventory
    WHERE product_id = NEW.product_id;
    
    IF available_quantity < NEW.quantity THEN
        RAISE EXCEPTION 'Недостаточно товара ID %: доступно %, требуется %', 
            NEW.product_id, available_quantity, NEW.quantity;
    END IF;
    
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trg_check_stock_before_order
BEFORE INSERT ON order_items
FOR EACH ROW
EXECUTE FUNCTION reserve_stock_on_order();

INSERT INTO system_settings (setting_key, setting_value, description) VALUES
('company_name', 'Складская Логистика ООО', 'Название компании'),
('default_warehouse', '1', 'ID основного склада по умолчанию'),
('currency', 'RUB', 'Валюта системы'),
('tax_rate', '20', 'НДС в процентах');

INSERT INTO users (username, email, password_hash, role, full_name, phone) VALUES
('admin', 'admin@warehouse.local', '$2a$12$YourHashedPasswordHere', 'admin', 'Администратор Системы', '+79991234567'),
('manager1', 'manager@warehouse.local', '$2a$12$YourHashedPasswordHere', 'manager', 'Менеджер Иванов', '+79991234568'),
('worker1', 'worker@warehouse.local', '$2a$12$YourHashedPasswordHere', 'warehouse_worker', 'Кладовщик Петров', '+79991234569');

DO $$
DECLARE
    admin_id INTEGER;
    manager_id INTEGER;
    worker_id INTEGER;
BEGIN
    SELECT user_id INTO admin_id FROM users WHERE username = 'admin';
    SELECT user_id INTO manager_id FROM users WHERE username = 'manager1';
    SELECT user_id INTO worker_id FROM users WHERE username = 'worker1';
    
    INSERT INTO employees (user_id, position, department, hire_date, salary) VALUES
    (admin_id, 'Системный администратор', 'IT', '2023-01-15', 80000),
    (manager_id, 'Менеджер склада', 'Логистика', '2023-02-20', 60000),
    (worker_id, 'Кладовщик', 'Логистика', '2023-03-10', 45000);
END $$;

INSERT INTO categories (name, description) VALUES
('Электроника', 'Электронные устройства и комплектующие'),
('Офисные товары', 'Канцелярия и офисное оборудование'),
('Хозтовары', 'Хозяйственные товары и инвентарь'),
('Упаковка', 'Упаковочные материалы');

INSERT INTO suppliers (name, contact_person, email, phone, address) VALUES
('ООО Электроникс', 'Сергей Иванов', 'info@electronix.ru', '+74951234567', 'Москва, ул. Ленина, 1'),
('Канцелярский мир', 'Ольга Петрова', 'sales@kancmir.ru', '+74957654321', 'Москва, пр. Мира, 15'),
('Упаковочные решения', 'Алексей Сидоров', 'pack@packing.ru', '+74959876543', 'Москва, ул. Промышленная, 10');

INSERT INTO warehouses (name, location, capacity, manager_id) VALUES
('Основной склад', 'Москва, складской комплекс №1', 10000, 
    (SELECT employee_id FROM employees WHERE position = 'Менеджер склада' LIMIT 1));

INSERT INTO storage_locations (warehouse_id, location_code, aisle, shelf, bin, max_capacity) VALUES
(1, 'A-01-01', 'A', '01', '01', 100),
(1, 'A-01-02', 'A', '01', '02', 100),
(1, 'B-02-01', 'B', '02', '01', 50),
(1, 'C-03-01', 'C', '03', '01', 200);

CREATE VIEW current_inventory AS
SELECT 
    p.product_id,
    p.sku,
    p.name AS product_name,
    c.name AS category,
    s.name AS supplier,
    COALESCE(SUM(pi.quantity), 0) AS total_quantity,
    p.unit_price,
    p.min_stock_level,
    p.max_stock_level,
    CASE 
        WHEN COALESCE(SUM(pi.quantity), 0) <= p.min_stock_level THEN 'Низкий запас'
        WHEN COALESCE(SUM(pi.quantity), 0) >= p.max_stock_level THEN 'Избыток'
        ELSE 'Норма'
    END AS stock_status
FROM products p
LEFT JOIN product_inventory pi ON p.product_id = pi.product_id
LEFT JOIN categories c ON p.category_id = c.category_id
LEFT JOIN suppliers s ON p.supplier_id = s.supplier_id
WHERE p.is_active = TRUE
GROUP BY p.product_id, p.sku, p.name, c.name, s.name, p.unit_price, p.min_stock_level, p.max_stock_level;

CREATE VIEW order_details AS
SELECT 
    o.order_id,
    o.order_number,
    o.order_date,
    cl.company_name AS client,
    o.status,
    o.total_amount,
    o.final_amount,
    o.payment_status,
    COUNT(oi.order_item_id) AS items_count,
    SUM(oi.quantity) AS total_quantity,
    e.full_name AS responsible_employee
FROM orders o
JOIN clients cl ON o.client_id = cl.client_id
LEFT JOIN order_items oi ON o.order_id = oi.order_id
LEFT JOIN employees e ON o.employee_id = e.employee_id
GROUP BY o.order_id, o.order_number, o.order_date, cl.company_name, o.status, 
         o.total_amount, o.final_amount, o.payment_status, e.full_name;

CREATE VIEW sales_report AS
SELECT 
    DATE(o.order_date) AS sale_date,
    EXTRACT(MONTH FROM o.order_date) AS month,
    EXTRACT(YEAR FROM o.order_date) AS year,
    COUNT(DISTINCT o.order_id) AS orders_count,
    SUM(o.final_amount) AS total_sales,
    SUM(oi.quantity) AS total_items_sold,
    AVG(o.final_amount) AS avg_order_value
FROM orders o
JOIN order_items oi ON o.order_id = oi.order_id
WHERE o.status NOT IN ('cancelled')
GROUP BY DATE(o.order_date), EXTRACT(MONTH FROM o.order_date), EXTRACT(YEAR FROM o.order_date);

**Ссылка на репозиторий:** [https://github.com/ваш-логин/warehouse-management-system](https://github.com/ваш-логин/warehouse-management-system)
