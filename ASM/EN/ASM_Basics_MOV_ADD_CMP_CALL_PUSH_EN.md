# 📝 ASM CheatSheet — MOV, ADD/SUB, CMP/JMP, CALL/RET, PUSH/POP

## 🔹 MOV
**What it does:**  
Copies data from source to destination. Source remains unchanged, only destination is modified.

**Formats:**  
- `MOV reg, reg` → register ← register  
- `MOV reg, mem` → register ← memory  
- `MOV mem, reg` → memory ← register  
- `MOV reg, imm` → register ← number  

**Examples:**  
```asm
MOV EAX, EBX
MOV EAX, [val]
MOV [val], EAX
MOV EAX, 123
```

**Common mistakes:**  
- Memory → memory not allowed directly, must use register.  
- Size mismatch (16/32/64).

**Tips:**  
- `MOVZX` — zero extension.  
- `MOVSX` — sign extension.  

**Key point:**  
`MOV` is the base instruction in ASM. Requires size match and usually one register.

---

## 🔹 ADD / SUB
**What they do:**  
- `ADD` adds.  
- `SUB` subtracts.  
Both update CPU flags (Zero, Carry, Overflow).

**Examples:**  
```asm
ADD EAX, 5
SUB EBX, EAX
```

**Mistakes:**  
- Overflow changes flags → must check them.

**Key point:**  
Arithmetic + flags → foundation of conditions and loops.

---

## 🔹 CMP / JMP
**What they do:**  
- `CMP` compares (like `SUB`, result not stored).  
- `JMP` unconditional jump.  
- `Jxx` (`JE`, `JNE`, `JG`, `JL`) conditional jumps.  

**Examples:**  
```asm
CMP EAX, EBX
JE equal
JNE notequal
JMP end
```

**Mistakes:**  
- Must use `Jxx` right after `CMP`, flags may change.

**Key point:**  
`CMP` + `Jxx` = foundation of `if`, `while`, `for`.

---

## 🔹 CALL / RET
**What they do:**  
- `CALL` calls a function (push return addr to stack).  
- `RET` returns (pop addr from stack).

**Examples:**  
```asm
CALL myfunc
...
myfunc:
    MOV EAX, 1
    RET
```

**Mistakes:**  
- Broken stack → wrong return → crash.

**Key point:**  
Functions exist thanks to `CALL` and `RET`.

---

## 🔹 PUSH / POP
**What they do:**  
- `PUSH` pushes value to stack.  
- `POP` pops value from stack.  

**Examples:**  
```asm
PUSH EAX
POP EBX     ; EBX = old EAX
```

**Mistakes:**  
- Imbalance in PUSH/POP breaks stack.

**Key point:**  
Stack operations = saving registers and function calls.

---

🕶 *With silence and precision. — SilentPuck*
