# HALCON
Es una distribuidora de materiales de construcción que requiere una aplicación web para automatizar sus procesos internos.
CREATE DATABASE IF NOT EXISTS HALCON;
USE HALCON;

CREATE TABLE IF NOT EXISTS Usuarios (
    IDUsuario INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(255) NOT NULL,
    Usuario VARCHAR(50) UNIQUE NOT NULL,
    Contraseña VARCHAR(100) NOT NULL
);

CREATE TABLE IF NOT EXISTS Clientes (
    IDCliente INT AUTO_INCREMENT PRIMARY KEY,
    NumeroCliente INT NOT NULL,
    NumeroFactura INT NOT NULL,
    Fecha DATE NOT NULL,
    CONSTRAINT FK_ClienteUsuario FOREIGN KEY (IDCliente) REFERENCES Usuarios(IDUsuario)
);

CREATE TABLE IF NOT EXISTS GestionPedidos (
    IDPedido INT AUTO_INCREMENT PRIMARY KEY,
    Pedidos VARCHAR(255) NOT NULL,
    Ruta VARCHAR(100) NOT NULL,
    Direccion VARCHAR(255) NOT NULL,
    Entregado BOOLEAN NOT NULL,
    CONSTRAINT FK_PedidoUsuario FOREIGN KEY (IDPedido) REFERENCES Usuarios(IDUsuario)
);

CREATE TABLE IF NOT EXISTS PanelAdministrativo (
    IDPanel INT AUTO_INCREMENT PRIMARY KEY,
    Roles VARCHAR(100) NOT NULL,
    Compras BOOLEAN NOT NULL,
    Ventas BOOLEAN NOT NULL,
    Almacen BOOLEAN NOT NULL,
    Rutas BOOLEAN NOT NULL,
    CONSTRAINT FK_PanelUsuario FOREIGN KEY (IDPanel) REFERENCES Usuarios(IDUsuario)
);
SELECT*FROM usuarios;
SELECT*FROM clientes;
