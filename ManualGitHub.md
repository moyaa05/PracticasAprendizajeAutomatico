# 📘 Manual de Supervivencia Git para Parejas (Terminal Edition)

> **Regla de Oro:** Nunca trabajes directamente en la rama `main`. Úsala solo para recibir trabajo terminado.

---

## 1. Antes de empezar (Preparación diaria)
Cada vez que te sientes a trabajar, limpia tu entorno para evitar conflictos con tu compañero.

```bash
# 1. Ve a la rama principal
git checkout main

# 2. Descarga lo último de la nube (por si tu compañero fusionó algo)
git pull origin main

# 3. Elige tu camino:
# A) Si empiezas una TAREA NUEVA:
git checkout -b nombre-de-la-rama  # (Ej: PR3, diseño-login)

# B) Si sigues con una TAREA PENDIENTE:
git checkout nombre-de-la-rama
git pull origin nombre-de-la-rama  # (Bájate lo que haya hecho tu colega)
````

-----

## 2\. El Ciclo de Trabajo (Bucle Infinito)

Mientras estás en tu rama (ej: `PR3`), este es tu taller sucio. Puedes repetir esto 200 veces.

### A. Guardar tu trabajo (Local)

```bash
git add .
git commit -m "Descripción clara de lo que hiciste"
```

### B. Sincronizarte con tu colega

Si ambos estáis tocando la **misma rama**, necesitáis pasaros el código constantemente.

**Para ENVIAR tus cambios:**

```bash
git push origin nombre-de-la-rama
# Nota: Si es la primera vez que la subes, usa: git push -u origin nombre-de-la-rama
```

**Para RECIBIR los cambios de tu colega:**

```bash
git pull origin nombre-de-la-rama
```

-----

## 3\. Cerrar la Tarea (El Merge)

Solo cuando la práctica esté **terminada y funcione perfecta**.

1.  **Sube todo:** Asegúrate de hacer un último `git push` en tu rama.
2.  **Ve a GitHub (Web):**
      * Pulsa el botón verde **"Compare & pull request"**.
      * Comprueba que la base sea `main`.
      * Avisa a tu colega para que revise.
      * Pulsa **"Merge pull request"**.
3.  **Limpieza Final (En tu terminal):**
    ```bash
    git checkout main
    git pull origin main       # Actualizas tu main con la fusión oficial
    git branch -d nombre-rama  # Borras la rama vieja (opcional)
    git fetch -p               # Limpias referencias fantasma
    ```

-----

## 🚨 Kit de Emergencias (Solución de Problemas)

### "Me dice que la rama ya existe"

Si quieres sobrescribirla a la fuerza (borrando lo que hubiera antes):

```bash
git branch -M nombre-de-la-rama
```

### "Hice commit en la rama equivocada (o en main)"

Deshaz el commit pero **guarda tus cambios** para moverlos a la rama correcta:

```bash
# 1. Deshaz el commit (vuelve atrás en el tiempo)
git reset --soft HEAD~1

# 2. Crea la rama correcta (se lleva tus cambios automáticamente)
git checkout -b rama-correcta

# 3. Haz el commit de nuevo
git commit -m "Ahora sí en el sitio correcto"
```

### "Quiero cambiar el nombre de una rama"

1.  Renómbrala en tu PC: `git branch -m nuevo-nombre`
2.  Si ya estaba subida a GitHub:
    ```bash
    git push origin -u nuevo-nombre        # Subes la nueva
    git push origin --delete nombre-viejo  # Borras la vieja
    ```

### "¡CONFLICTO\!" (Al hacer pull o merge)

No entres en pánico.

1.  Abre el archivo en tu editor de código.
2.  Busca las marcas `<<<<<<< HEAD` y `>>>>>>>`.
3.  Borra las líneas que sobran y deja el código como debe quedar.
4.  Guarda el archivo y ejecuta:
    ```bash
    git add .
    git commit -m "Conflicto arreglado"
    ```

-----

## ⚡ Cheatsheet Rápido

| Acción | Comando |
| :--- | :--- |
| **Ver estado** | `git status` |
| **Ver ramas** | `git branch` (o `git branch -a` para ver todas) |
| **Cambiar rama** | `git checkout nombre-rama` |
| **Crear rama** | `git checkout -b nombre-rama` |
| **Guardar** | `git add .` + `git commit -m "msg"` |
| **Subir** | `git push origin nombre-rama` |
| **Bajar** | `git pull origin nombre-rama` |

```
```