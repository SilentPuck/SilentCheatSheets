# Hoja de trucos: Generación de números aleatorios en C++ moderno (`<random>`)

Breve y claro — para orientarse rápidamente al desarrollar herramientas serias.
---

## Qué es y para qué sirve
- `<random>` (C++11+) — biblioteca moderna para aleatoriedad pseudo y (parcialmente) de hardware.  
- Usos: simulaciones, juegos, pruebas, generación de contraseñas/PIN (con advertencias), estadística.  
- Para **criptografía**, `<random>` por sí solo no garantiza seguridad; se necesitan fuentes y bibliotecas criptográficamente seguras.

---

## Componentes principales (conceptualmente)
1. **Fuente de entropía / semilla** — valor inicial que determina la secuencia.  
   - `std::random_device rd;` — intenta obtener una fuente del sistema (ej. `/dev/urandom`, WinAPI).  
2. **Generador (motor PRNG)** — produce un flujo de bits pseudoaleatorios.  
   - Ejemplos: `std::mt19937` (32-bit), `std::mt19937_64` (64-bit), `std::minstd_rand0`, `std::ranlux48`.  
3. **Distribución** — traduce bits en números dentro de un rango/distribución deseado.  
   - `std::uniform_int_distribution<>` — enteros uniformes.  
   - `std::uniform_real_distribution<>` — reales uniformes.  
   - `std::normal_distribution<>` — normal (Gauss), etc.

---

## Recomendaciones
- Para la mayoría de tareas (velocidad + calidad) → `std::mt19937` o `std::mt19937_64`.  
- Si necesitas mayor período o 64-bit → usa `mt19937_64`.  
- Para claves críticas → usa APIs específicas (cripto del SO, OpenSSL, libsodium), no `mt19937`.

---

## Patrón de uso (pasos, sin código completo)
1. *Obtener semilla*: `std::random_device rd;`  
2. *Inicializar generador*: `std::mt19937 gen(rd());`  
3. *Crear distribución*: `std::uniform_int_distribution<int> dist(min, max);`  
4. *Generar número*: `int x = dist(gen);`  
5. *Para N números* — llama `dist(gen)` en un bucle.

> Nota: `random_device` puede ser lento o pseudo en algunas plataformas; aún así es mejor que `time()`.

---

## Ejemplos de rangos
- PIN (4 dígitos): `dist(0, 9999)` → formatea ceros a la izquierda aparte.  
- Captcha / id único: `dist(100000, 999999)` (6 dígitos).  
- Valores de prueba: `[1, 100]`, `[0, RAND_MAX]`, etc.

---

## Seguridad
- `mt19937` es determinista: con la semilla se puede reconstruir toda la secuencia.  
- Para seguridad (claves, tokens, contraseñas):  
  - Usa `std::random_device` como fuente (si el SO garantiza criptoseguridad), o  
  - usa `CryptGenRandom` / `BCryptGenRandom` en Windows, `/dev/urandom` o libsodium/openssl en Unix.  
- Nunca uses `rand()`/`srand()` para fines criptográficos.

---

## Errores comunes
- **No especificar rango** en distribución — no funciona; siempre indica `min/max`.  
- **Seed = time(0) sin cast** — MSVC avisa; usa `static_cast<unsigned int>(time(0))`, pero mejor `random_device`.  
- **Crear generador en bucle**: si reinicializas `gen` con `random_device` en cada iteración, pierdes rendimiento; crea uno y reutilízalo.  
- **Fuente de semilla débil**: si `random_device` es pseudo, busca fuente externa.

---

## Referencia rápida
- `std::random_device rd;` — fuente de entropía (puede ser lenta/pseudo).  
- `std::mt19937 gen(rd());` — generador (32-bit).  
- `std::mt19937_64 gen64(rd());` — generador 64-bit.  
- `std::uniform_int_distribution<int> dist(a, b);` — enteros uniformes en `[a, b]`.  
- `std::uniform_real_distribution<double> dist(0.0, 1.0);` — reales uniformes en `[0.0, 1.0]`.  
- Uso: `auto val = dist(gen);`

---

## Patrones de uso (pasos + ejemplos)
### Generar N números aleatorios 1–100
1. Crear `std::random_device rd;`
2. Crear `std::mt19937 gen(rd());`
3. Crear `std::uniform_int_distribution<int> dist(1, 100);`
4. Bucle `for i in 0..N-1` — `print(dist(gen))`

### Generar PIN de dígitos
1. Crear `dist(0, 9)` y llamarlo 4 veces, juntando dígitos.  
2. Alternativa: `dist(0, 9999)` y luego imprimir con ceros a la izquierda.

### Si necesitas criptoseguridad
1. No confíes en `mt19937`.  
2. Usa API cripto del SO o libsodium: pide bytes aleatorios y convierte.

---

## Verificación rápida (práctica)
- Validar generador con tests estadísticos simples (suma, media, distribución).  
- `mt19937` con semilla de `random_device` es suficiente para la mayoría de casos no críticos.

---

## Checklist antes de usar
- [ ] ¿Nivel de seguridad definido (juego/prueba/claves)?  
- [ ] ¿Generador elegido (`mt19937` / `mt19937_64` / API cripto)?  
- [ ] ¿Distribución y rango configurados explícitamente?  
- [ ] ¿Generador/distribución inicializados una sola vez?  
- [ ] ¿No se usa `rand()`/`srand()` en módulos nuevos?  
- [ ] ¿Bibliotecas cripto externas usadas si es necesario?

---

## Más adelante
- Revisa el comportamiento de `std::random_device` en tu SO (Windows vs Linux).  
- Explora otras distribuciones: `normal_distribution`, `bernoulli_distribution`, `poisson_distribution`.  
- Para cripto: estudia OpenSSL `RAND_bytes` o libsodium `randombytes_buf()`.
