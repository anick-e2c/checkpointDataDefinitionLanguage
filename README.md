# checkpointDataDefinitionLanguage


#### 1. Création des tables avec contraintes

# -- Table CUSTOMER
CREATE TABLE Customer (
    Customer_id     VARCHAR2(20) PRIMARY KEY,
    Customer_Name   VARCHAR2(20) NOT NULL,
    Customer_Tel    NUMBER
);


# -- Table PRODUCT
CREATE TABLE Product (
    Product_id      VARCHAR2(20) PRIMARY KEY,
    Product_Name    VARCHAR2(20) NOT NULL,
    Price           NUMBER CHECK (Price > 0)
);


# -- Table ORDERS
CREATE TABLE Orders (
    Customer_id     VARCHAR2(20),
    Product_id      VARCHAR2(20),
    Quantity        NUMBER,
    Total_amount    NUMBER,
    CONSTRAINT pk_orders PRIMARY KEY (Customer_id, Product_id),
    CONSTRAINT fk_orders_customer FOREIGN KEY (Customer_id) REFERENCES Customer(Customer_id),
    CONSTRAINT fk_orders_product FOREIGN KEY (Product_id) REFERENCES Product(Product_id)
);


### 2. Ajout des colonnes demandées

# -- Ajouter une colonne Catégorie à la table Product

ALTER TABLE Product ADD Category VARCHAR2(20);

# -- Ajouter une colonne OrderDate à la table Orders avec valeur par défaut

ALTER TABLE Orders ADD OrderDate DATE DEFAULT SYSDATE;
