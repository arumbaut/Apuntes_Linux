Encontrar rutas especifacas
```
find / -type d -path "*/Cargas/JAZZPLAT/Guadalajara/Auditoria" 2>/dev/null
```


### **Buscar por nombre de archivo**

```
find /ruta -name "archivo.txt"
```

Busca un archivo con nombre exacto en una ruta específica.

```
find /ruta -iname "archivo.txt"
```

### **Buscar por tipo de archivo**

```
find /ruta -type f     # Archivos normales 
find /ruta -type d     # Directorios 
find /ruta -type l     # Enlaces simbólicos
```

### **Buscar por tamaño**

```
find /ruta -size +100M     # Archivos mayores a 100 MB 
find /ruta -size -10k      # Archivos menores a 10 KB
```

### **Buscar por fecha de modificación/acceso/cambio**

```
find /ruta -mtime -7       # Modificados en los últimos 7 días 
find /ruta -atime +30      # Accedidos hace más de 30 días 
find /ruta -ctime 0        # Cambiados hoy
```

### **Buscar por permisos**

```
find /ruta -perm 644       # Archivos con permisos exactos 644 
find /ruta -perm -4000     # Archivos con SUID activo
```

### **Buscar por propietario o grupo**

```
find /ruta -user usuario 
find /ruta -group grupo
```

### **Ejecutar comandos sobre los archivos encontrados**

 Borra todos los archivos `.log`.
```
find /ruta -name "*.log" -exec rm -f {} \;
```


Cambia permisos a todos los archivos encontrados.
```
find /ruta -type f -exec chmod 644 {} \;
```

### **Buscar archivos vacíos**

```
find /ruta -type f -empty
```

### **Limitar profundidad de búsqueda**

```
find /ruta -maxdepth 1 -name "*.conf"
```

### **Combinar múltiples condiciones**

```
find /ruta \( -name "*.log" -o -name "*.bak" \) -type f -delete
```