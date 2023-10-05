CREATE TABLE doctors (id int(11) NOT NULL AUTO_INCREMENT, name varchar(225) NOT NULL, phone int(20) NOT NULL UNIQUE, addres text NOT NULL, nid int(11) NOT NULL UNIQUE, created datetime NOT NULL, modified datetime NOT NULL, specialistsid int(11) NOT NULL, PRIMARY KEY (id), INDEX (name));
CREATE TABLE drug_orders (id int(11) NOT NULL AUTO_INCREMENT, created int(11) NOT NULL, pharmacist_id int(11) NOT NULL, medical_records_id int(11) NOT NULL, drugs_id int(11) NOT NULL, PRIMARY KEY (id));
CREATE TABLE drugs (id int(11) NOT NULL AUTO_INCREMENT, name varchar(225) NOT NULL, type int(11) NOT NULL, price int(11) NOT NULL, stock int(11) NOT NULL, created datetime NOT NULL, modified datetime NOT NULL, PRIMARY KEY (id), INDEX (name));
CREATE TABLE medical_records (id int(11) NOT NULL AUTO_INCREMENT, `date` datetime NOT NULL, complaint text NOT NULL, created datetime NOT NULL, modified datetime NOT NULL, patients_id int(11) NOT NULL, doctor_id int(11) NOT NULL, PRIMARY KEY (id));
CREATE TABLE patients (id int(11) NOT NULL AUTO_INCREMENT, name varchar(225) NOT NULL, addres text NOT NULL, gender varchar(255) NOT NULL, birth_date datetime NOT NULL, phone varchar(20) NOT NULL UNIQUE, complaint varchar(255) NOT NULL, created datetime NOT NULL, modified datetime NOT NULL, PRIMARY KEY (id), INDEX (name));
CREATE TABLE pharmacists (id int(11) NOT NULL AUTO_INCREMENT, name varchar(225) NOT NULL, phone varchar(20) NOT NULL, created int(11) NOT NULL, modified int(11) NOT NULL, addres text NOT NULL, PRIMARY KEY (id), INDEX (name));
CREATE TABLE specialists (id int(11) NOT NULL AUTO_INCREMENT, name varchar(225) NOT NULL, created datetime NOT NULL, modified datetime NOT NULL, PRIMARY KEY (id), INDEX (name));
ALTER TABLE medical_records ADD CONSTRAINT FKmedical_re935762 FOREIGN KEY (patients_id) REFERENCES patients (id);
ALTER TABLE medical_records ADD CONSTRAINT FKmedical_re314054 FOREIGN KEY (doctor_id) REFERENCES doctors (id);
ALTER TABLE drug_orders ADD CONSTRAINT FKdrug_order956032 FOREIGN KEY (pharmacist_id) REFERENCES pharmacists (id);
ALTER TABLE drug_orders ADD CONSTRAINT FKdrug_order680659 FOREIGN KEY (medical_records_id) REFERENCES medical_records (id);
ALTER TABLE doctors ADD CONSTRAINT FKdoctors142438 FOREIGN KEY (specialistsid) REFERENCES specialists (id);
ALTER TABLE drug_orders ADD CONSTRAINT FKdrug_order748803 FOREIGN KEY (drugs_id) REFERENCES drugs (id);

