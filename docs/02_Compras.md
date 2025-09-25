# 📑 Módulo de Compras

El módulo de **Compras** permite registrar y consultar todos los gastos relacionados con la adquisición de insumos para la finca.  

## 🎯 Objetivo
Centralizar la información de compras (insumos, alimentos, etc.), vinculando cada registro con proveedor y destino, y calcular automáticamente los costos individuales y totales.  

## 📂 Estructura de la tabla
La tabla **Compras** tiene los siguientes campos:

| Campo          | Tipo de dato       | Descripción |
|----------------|-------------------|-------------|
| `ID_Compra`    | Texto (autogenerado) | Identificador único de la compra. Se genera automáticamente al abrir el formulario, pero puede ser editado. |
| `Fecha`        | Fecha              | Día en que se realizó la compra. |
| `Descripción`  | Texto              | Detalle del producto o insumo comprado. |
| `Cantidad`     | Número entero      | Número de unidades adquiridas. |
| `V/Unitario`   | Número (moneda)    | Valor unitario del producto adquirido. |
| `Costo_Total`  | Número (calculado) | Multiplicación automática de `Cantidad * V/Unitario`. |
| `Proveedor`    | Referencia (tabla Proveedores) | Nombre del proveedor al que se le compró. |
| `Destino`      | Referencia (tabla Destino) | Área o especie (ejemplo: porcinos, insumos, etc.) a la que se destina la compra. |
| `Total_Compras`| Número (acumulado) | Suma progresiva de todas las compras registradas. Campo de solo lectura. |

## 🖥️ Interfaz en AppSheet
- La vista **Compras** muestra una tabla con los campos más relevantes: Fecha, Descripción, Cantidad, V/Unitario, Costo_Total, Proveedor y Destino.  
- El botón **Add (+)** abre el formulario de captura.  

## 📝 Formulario de Compras
El formulario permite ingresar o editar los siguientes datos:  
1. **ID_Compra** → generado automáticamente, editable.  
2. **Fecha** → seleccionable en calendario.  
3. **Descripción** → campo libre para detallar el insumo.  
4. **Cantidad** → campo numérico con incrementadores (+ / –).  
5. **V/Unitario** → campo numérico en formato moneda.  
6. **Costo_Total** → calculado automáticamente (no editable).  
7. **Proveedor** → desplegable, referencia a tabla **Proveedores**.  
8. **Destino** → desplegable, referencia a tabla **Destino**.  
9. **Total_Compras** → suma acumulada, campo bloqueado.  

## ⚙️ Reglas de negocio
- `Costo_Total = Cantidad * V/Unitario` (cálculo automático).  
- `Total_Compras` se actualiza como suma acumulada de todos los registros.  
- La consistencia de **Proveedor** y **Destino** se asegura mediante tablas relacionadas.  
