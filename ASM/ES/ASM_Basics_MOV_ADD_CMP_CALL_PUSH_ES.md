# 📝 ASM Hoja de trucos — MOV, ADD/SUB, CMP/JMP, CALL/RET, PUSH/POP

## 🔹 MOV
**Qué hace:**  
Copia datos de un lugar a otro. El origen no cambia, solo el destino.

**Formatos:**  
- `MOV reg, reg` → registro ← registro  
- `MOV reg, mem` → registro ← memoria  
- `MOV mem, reg` → memoria ← registro  
- `MOV reg, imm` → registro ← número  

**Ejemplos:**  
```asm
MOV EAX, EBX
MOV EAX, [val]
MOV [val], EAX
MOV EAX, 123
```

**Errores comunes:**  
- Memoria → memoria no permitido directamente, usar registro.  
- Tamaños deben coincidir (16/32/64).

**Trucos:**  
- `MOVZX` — extensión con ceros.  
- `MOVSX` — extensión con signo.  

**Clave:**  
`MOV` es la instrucción base, está en todas partes.

---

## 🔹 ADD / SUB
**Qué hacen:**  
- `ADD` suma.  
- `SUB` resta.  
Ambas actualizan banderas (Zero, Carry, Overflow).

**Ejemplos:**  
```asm
ADD EAX, 5
SUB EBX, EAX
```

**Errores:**  
- El desbordamiento cambia banderas.

**Clave:**  
Aritmética + banderas = base de condiciones y bucles.

---

## 🔹 CMP / JMP
**Qué hacen:**  
- `CMP` compara (como `SUB`, no guarda resultado).  
- `JMP` salto incondicional.  
- `Jxx` (`JE`, `JNE`, `JG`, `JL`) saltos condicionales.  

**Ejemplos:**  
```asm
CMP EAX, EBX
JE equal
JNE notequal
JMP end
```

**Errores:**  
- Usar `Jxx` justo después de `CMP`.

**Clave:**  
`CMP` + `Jxx` = base de `if`, `while`, `for`.

---

## 🔹 CALL / RET
**Qué hacen:**  
- `CALL` llama función (guarda dirección en pila).  
- `RET` retorna (saca dirección de pila).

**Ejemplos:**  
```asm
CALL myfunc
...
myfunc:
    MOV EAX, 1
    RET
```

**Errores:**  
- Pila dañada = retorno incorrecto.

**Clave:**  
Funciones existen gracias a `CALL` y `RET`.

---

## 🔹 PUSH / POP
**Qué hacen:**  
- `PUSH` mete valor en pila.  
- `POP` saca valor de pila.  

**Ejemplos:**  
```asm
PUSH EAX
POP EBX     ; EBX = valor viejo de EAX
```

**Errores:**  
- Desbalance en PUSH/POP rompe la pila.

**Clave:**  
Operaciones de pila = base de funciones y registros guardados.

---

🕶 *With silence and precision. — SilentPuck*
