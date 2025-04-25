# CORREO.SH


El correo será enviado **desde tu servidor usando `mail` y Postfix**.

---

### ✅ Script: `enviar_correo.sh`

```bash
#!/bin/bash

# Solicitar datos al usuario
read -p "¿A quién se enviará el correo? (ej. usuario@dominio.com): " destinatario
read -p "Asunto del correo: " asunto
read -p "Escribe el cuerpo del mensaje: " cuerpo

# Obtener hora actual
hora_actual=$(date +"%Y-%m-%d %H:%M:%S")

# Construir el mensaje completo
mensaje="$cuerpo

[Enviado automáticamente a las $hora_actual]"

# Enviar correo con mailutils o mailx
echo "$mensaje" | mail -s "$asunto" "$destinatario"

echo "Correo enviado a $destinatario."
```

---

### 📌 Requisitos previos:

1. **Postfix ya configurado** en tu Debian 12 (lo tienes).
2. Instala `mailutils` si no lo tienes:
   ```bash
   sudo apt update
   sudo apt install mailutils
   ```

---

### 🔧 ¿Cómo hacerlo?

Si guardaste el script como `enviar_correo.sh`, entonces haz esto:

```bash
chmod +x enviar_correo.sh
```

Luego ya puedes ejecutarlo con:

```bash
./enviar_correo.sh
```

Y si quieres probar que se está enviando correctamente, puedes dejar fijo el destinatario para pruebas, o revisar los logs de correo con:

```bash
tail -f /var/log/mail.log
```
