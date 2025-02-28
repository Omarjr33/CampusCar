[![](https://mermaid.ink/img/pako:eNp9VdtO4zAQ_ZXIzwW19J43RLPailJWUHhYVYpce2itdTyR46CF0n_fSS_bpE7IQxJ7bmfOzNhbJlACCxnYieJry5OlCeh5jX5O715mj8H2sC4eZVzwDhslco2xksGv-7Msc1aZdfCuTPDibyfcCu7vUmSNVf_cqNKOBKESroPU0g96DgRqtN6uUynGApNVnjm10lCv4Cw3WaIyhcZTgMxxWQq3QtTATSBVlqI5-9wdPof33WwazRfRJWFCKzAOGvgyBNPWIAQNb2j8jCHhSnu7UhE_4n8mFViv0XwSTR6f_EIaCRJtE7A8AYsxJCllLrGuqJfYJXcQvIHYcGLfEL-ON2Na3NYAcvwSTcnnXu63hkPHfUYScCgxTvkaG8vx476ZkZOsAnsSLW5nsyiuhS-BcGiIa9Oo5OfHPY9UWVZt_nL-FVTP0dPr9G76GD_cUvvNpw9FG3pzm4F9V4Wb-nLvR-KkU0t_jfCIT2Dm_E6VkAmrUlGZr-_S9aoTLNn8ZTZbstoOOh5PX19XV7i9KE1IphkcChqAOXm4NGpgrrAuKF_ByfA02ke7cxALXKtP3qD3jf8MNZHp-BnacUq9EGs6jIjDsiZJGtMuJo84JOisxWiE6byQdLrvu2HJ3AYSEhWKkts_hc8d6fHc4fOHESx0NocWs5ivNyx84zqjVZ4WbXC8HU4qKTe_EctLFm7ZXxbedHrXg_FNtzsa9vqdzrjdbbEPFg6vO-PxYNgbD3r0HQxHuxb73DtoX49H_Xa_1-7ejHqd_nBABiCVQ_twuJn2F9TuH5yl_pk?type=png)](https://mermaid.live/edit#pako:eNp9VdtO4zAQ_ZXIzwW19J43RLPailJWUHhYVYpce2itdTyR46CF0n_fSS_bpE7IQxJ7bmfOzNhbJlACCxnYieJry5OlCeh5jX5O715mj8H2sC4eZVzwDhslco2xksGv-7Msc1aZdfCuTPDibyfcCu7vUmSNVf_cqNKOBKESroPU0g96DgRqtN6uUynGApNVnjm10lCv4Cw3WaIyhcZTgMxxWQq3QtTATSBVlqI5-9wdPof33WwazRfRJWFCKzAOGvgyBNPWIAQNb2j8jCHhSnu7UhE_4n8mFViv0XwSTR6f_EIaCRJtE7A8AYsxJCllLrGuqJfYJXcQvIHYcGLfEL-ON2Na3NYAcvwSTcnnXu63hkPHfUYScCgxTvkaG8vx476ZkZOsAnsSLW5nsyiuhS-BcGiIa9Oo5OfHPY9UWVZt_nL-FVTP0dPr9G76GD_cUvvNpw9FG3pzm4F9V4Wb-nLvR-KkU0t_jfCIT2Dm_E6VkAmrUlGZr-_S9aoTLNn8ZTZbstoOOh5PX19XV7i9KE1IphkcChqAOXm4NGpgrrAuKF_ByfA02ke7cxALXKtP3qD3jf8MNZHp-BnacUq9EGs6jIjDsiZJGtMuJo84JOisxWiE6byQdLrvu2HJ3AYSEhWKkts_hc8d6fHc4fOHESx0NocWs5ivNyx84zqjVZ4WbXC8HU4qKTe_EctLFm7ZXxbedHrXg_FNtzsa9vqdzrjdbbEPFg6vO-PxYNgbD3r0HQxHuxb73DtoX49H_Xa_1-7ejHqd_nBABiCVQ_twuJn2F9TuH5yl_pk)



# Documentación del Diseño de la Base de Datos para Concesionario de Vehículos

## 1. Justificación del Diseño

El diseño de la base de datos para el concesionario de vehículos se ha estructurado considerando las entidades principales del negocio: vehículos, clientes, vendedores, ventas y servicios de mantenimiento. A continuación, se detalla la justificación de este diseño:

### 1.1 Estructura de Tablas

Se han definido 6 tablas principales:

- **VEHICULO**: Almacena toda la información relacionada con los vehículos disponibles en el concesionario.
- **CLIENTE**: Contiene los datos de contacto de los clientes del concesionario.
- **VENDEDOR**: Registra la información de los empleados que realizan ventas.
- **VENTA**: Almacena las transacciones de venta realizadas.
- **DETALLE_VENTA**: Implementa una relación muchos a muchos entre VENTA y VEHICULO, permitiendo que una venta pueda incluir múltiples vehículos.
- **SERVICIO_MANTENIMIENTO**: Registra los servicios de mantenimiento realizados a los vehículos.

### 1.2 Decisiones de Diseño

1. **Separación de VENTA y DETALLE_VENTA**: 
   - Se ha implementado el patrón cabecera-detalle para las ventas, permitiendo que una venta pueda incluir múltiples vehículos.
   - Esta estructura facilita el cálculo del total de venta y mantiene la integridad de los datos.

2. **Campo `disponible` en VEHICULO**:
   - Se ha añadido un campo booleano `disponible` para indicar si un vehículo está disponible para la venta.
   - Este campo se actualizará automáticamente cuando un vehículo sea vendido.

3. **Cliente opcional en SERVICIO_MANTENIMIENTO**:
   - Se permite que un servicio de mantenimiento pueda estar asociado opcionalmente a un cliente, contemplando el caso de vehículos en inventario no vendidos.

4. **Precio de venta en DETALLE_VENTA**:
   - Aunque el vehículo tiene un precio base, se almacena el precio final de venta en DETALLE_VENTA para mantener un registro histórico y permitir descuentos o negociaciones.

## 2. Restricciones y Validaciones

### 2.1 Claves Primarias

- **vehiculo_id**: Clave primaria de la tabla VEHICULO.
- **cliente_id**: Clave primaria de la tabla CLIENTE.
- **vendedor_id**: Clave primaria de la tabla VENDEDOR.
- **venta_id**: Clave primaria de la tabla VENTA.
- **detalle_venta_id**: Clave primaria de la tabla DETALLE_VENTA.
- **servicio_id**: Clave primaria de la tabla SERVICIO_MANTENIMIENTO.

### 2.2 Claves Únicas

- **vin**: Número de serie único (VIN) para cada vehículo.
- **numero_empleado**: Identificador único para cada vendedor.

### 2.3 Claves Foráneas

- **VENTA.cliente_id → CLIENTE.cliente_id**: Asocia una venta con un cliente.
- **VENTA.vendedor_id → VENDEDOR.vendedor_id**: Asocia una venta con un vendedor.
- **DETALLE_VENTA.venta_id → VENTA.venta_id**: Asocia un detalle de venta con una venta.
- **DETALLE_VENTA.vehiculo_id → VEHICULO.vehiculo_id**: Asocia un detalle de venta con un vehículo.
- **SERVICIO_MANTENIMIENTO.vehiculo_id → VEHICULO.vehiculo_id**: Asocia un servicio con un vehículo.
- **SERVICIO_MANTENIMIENTO.cliente_id → CLIENTE.cliente_id**: Asocia opcionalmente un servicio con un cliente.

### 2.4 Otras Restricciones

- **CHECK en VEHICULO.estado**: Asegura que el estado del vehículo sea 'nuevo' o 'usado'.
- **CHECK en VENTA.metodo_pago**: Asegura que el método de pago sea uno de los permitidos ('tarjeta', 'transferencia', 'efectivo', etc.).
- **CHECK en VEHICULO.anio**: Asegura que el año del vehículo sea válido.
- **CHECK en VEHICULO.precio y VENTA.total**: Asegura que los precios sean positivos.

## 3. Relaciones UML

### 3.1 Relación VEHICULO - DETALLE_VENTA (1:N)

- Un vehículo puede estar en un único detalle de venta (después de ser vendido).
- Un detalle de venta debe estar asociado exactamente a un vehículo.

### 3.2 Relación CLIENTE - VENTA (1:N)

- Un cliente puede realizar múltiples ventas.
- Una venta debe estar asociada exactamente a un cliente.

### 3.3 Relación VENDEDOR - VENTA (1:N)

- Un vendedor puede gestionar múltiples ventas.
- Una venta debe estar asociada exactamente a un vendedor.

### 3.4 Relación VENTA - DETALLE_VENTA (1:N)

- Una venta puede contener múltiples detalles de venta.
- Un detalle de venta debe estar asociado exactamente a una venta.

### 3.5 Relación VEHICULO - SERVICIO_MANTENIMIENTO (1:N)

- Un vehículo puede recibir múltiples servicios de mantenimiento.
- Un servicio de mantenimiento debe estar asociado exactamente a un vehículo.

### 3.6 Relación CLIENTE - SERVICIO_MANTENIMIENTO (1:N, opcional)

- Un cliente puede solicitar múltiples servicios de mantenimiento.
- Un servicio de mantenimiento puede estar asociado opcionalmente a un cliente (en caso de vehículos no vendidos).

## 4. Operaciones y Funcionalidades

### 4.1 Registro de Venta

Cuando se registra una venta:
1. Se crea un registro en la tabla VENTA.
2. Se crean uno o más registros en la tabla DETALLE_VENTA.
3. Se actualiza el campo `disponible` de los vehículos vendidos a FALSE.

### 4.2 Registro de Servicio de Mantenimiento

Se puede registrar un servicio de mantenimiento para:
1. Un vehículo vendido (asociado a un cliente).
2. Un vehículo en inventario (sin cliente asociado).

### 4.3 Consultas Importantes

El diseño permite realizar fácilmente consultas como:
- Ventas realizadas por un vendedor en un período.
- Vehículos disponibles por marca, modelo, año, etc.
- Historial de mantenimiento de un vehículo.
- Historial de compras de un cliente.





CREATE DATABASE ConcesionarioVehiculos;
USE ConcesionarioVehiculos;


CREATE TABLE VEHICULO (
    vehiculo_id INT AUTO_INCREMENT PRIMARY KEY,
    vin VARCHAR(17) NOT NULL UNIQUE,
    marca VARCHAR(50) NOT NULL,
    modelo VARCHAR(50) NOT NULL,
    anio INT NOT NULL,
    precio DECIMAL(12, 2) NOT NULL,
    color VARCHAR(30) NOT NULL,
    tipo_combustible VARCHAR(20) NOT NULL,
    tipo_transmision VARCHAR(20) NOT NULL,
    estado VARCHAR(10) NOT NULL,
    disponible BOOLEAN NOT NULL DEFAULT TRUE,
    CONSTRAINT chk_vehiculo_estado CHECK (estado IN ('nuevo', 'usado')),
    CONSTRAINT chk_vehiculo_anio CHECK (anio BETWEEN 1900 AND YEAR(CURDATE())+1),
    CONSTRAINT chk_vehiculo_precio CHECK (precio > 0)
);


CREATE TABLE CLIENTE (
    cliente_id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    telefono VARCHAR(15) NOT NULL,
    email VARCHAR(100) NOT NULL,
    direccion VARCHAR(200) NOT NULL
);


CREATE TABLE VENDEDOR (
    vendedor_id INT AUTO_INCREMENT PRIMARY KEY,
    numero_empleado VARCHAR(20) NOT NULL UNIQUE,
    nombre VARCHAR(100) NOT NULL,
    fecha_contratacion DATE NOT NULL
);


CREATE TABLE VENTA (
    venta_id INT AUTO_INCREMENT PRIMARY KEY,
    fecha_venta DATE NOT NULL,
    total DECIMAL(12, 2) NOT NULL,
    metodo_pago VARCHAR(20) NOT NULL,
    cliente_id INT NOT NULL,
    vendedor_id INT NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES CLIENTE(cliente_id),
    FOREIGN KEY (vendedor_id) REFERENCES VENDEDOR(vendedor_id),
    CONSTRAINT chk_venta_total CHECK (total > 0),
    CONSTRAINT chk_venta_metodo_pago CHECK (metodo_pago IN ('tarjeta', 'transferencia', 'efectivo', 'financiamiento'))
);


CREATE TABLE DETALLE_VENTA (
    detalle_venta_id INT AUTO_INCREMENT PRIMARY KEY,
    venta_id INT NOT NULL,
    vehiculo_id INT NOT NULL,
    precio_venta DECIMAL(12, 2) NOT NULL,
    FOREIGN KEY (venta_id) REFERENCES VENTA(venta_id),
    FOREIGN KEY (vehiculo_id) REFERENCES VEHICULO(vehiculo_id),
    CONSTRAINT chk_detalle_venta_precio CHECK (precio_venta > 0),
    CONSTRAINT uk_vehiculo_venta UNIQUE (vehiculo_id)
);


CREATE TABLE SERVICIO_MANTENIMIENTO (
    servicio_id INT AUTO_INCREMENT PRIMARY KEY,
    tipo_servicio VARCHAR(50) NOT NULL,
    fecha_servicio DATE NOT NULL,
    costo DECIMAL(10, 2) NOT NULL,
    descripcion TEXT,
    vehiculo_id INT NOT NULL,
    cliente_id INT,
    FOREIGN KEY (vehiculo_id) REFERENCES VEHICULO(vehiculo_id),
    FOREIGN KEY (cliente_id) REFERENCES CLIENTE(cliente_id),
    CONSTRAINT chk_servicio_costo CHECK (costo > 0),
    CONSTRAINT chk_tipo_servicio CHECK (tipo_servicio IN ('preventivo', 'correctivo', 'revision', 'garantia'))
);


DELIMITER //
CREATE TRIGGER after_detalle_venta_insert
AFTER INSERT ON DETALLE_VENTA
FOR EACH ROW
BEGIN
    UPDATE VEHICULO
    SET disponible = FALSE
    WHERE vehiculo_id = NEW.vehiculo_id;
END//
DELIMITER ;


DELIMITER //
CREATE TRIGGER before_detalle_venta_insert
BEFORE INSERT ON DETALLE_VENTA
FOR EACH ROW
BEGIN
    DECLARE is_available BOOLEAN;
    
    SELECT disponible INTO is_available
    FROM VEHICULO
    WHERE vehiculo_id = NEW.vehiculo_id;
    
    IF is_available = FALSE THEN
        SIGNAL SQLSTATE '45000' 
        SET MESSAGE_TEXT = 'No se puede vender un vehículo que no está disponible';
    END IF;
END//
DELIMITER ;


CREATE INDEX idx_vehiculo_marca_modelo ON VEHICULO(marca, modelo);
CREATE INDEX idx_vehiculo_disponible ON VEHICULO(disponible);
CREATE INDEX idx_venta_fecha ON VENTA(fecha_venta);
CREATE INDEX idx_venta_cliente ON VENTA(cliente_id);
CREATE INDEX idx_venta_vendedor ON VENTA(vendedor_id);
CREATE INDEX idx_servicio_vehiculo ON SERVICIO_MANTENIMIENTO(vehiculo_id);
CREATE INDEX idx_servicio_cliente ON SERVICIO_MANTENIMIENTO(cliente_id);
CREATE INDEX idx_servicio_fecha ON SERVICIO_MANTENIMIENTO(fecha_servicio);