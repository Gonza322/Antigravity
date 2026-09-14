# Flujo de Trabajo de Memoria (MEMORY_WORKFLOW.md)

Este documento define el ciclo de vida del contexto persistente y la documentaciÃ³n histÃ³rica por cada Consumer.

## Antes de iniciar una tarea

1. **Actualizar el contexto**:
   ```bash
   git -c safe.directory=D:/codex/Codex-Context-{consumer} -C D:\codex\Codex-Context-{consumer} pull --ff-only
   ```
2. **Lectura obligatoria**:
   - `PROJECT_MEMORY.md` (visiÃ³n consolidada, arquitectura y reglas transversales).
   - Este archivo (`MEMORY_WORKFLOW.md`).
3. **Revisar memorias histÃ³ricas**:
   - Carpeta `chats/` con los registros y decisiones previas relevantes.
4. **Inspeccionar cambios recientes**:
   - Ejecutar `git log` en el repositorio de contexto para detectar memorias incorporadas Ãºltimamente.
5. **VerificaciÃ³n tÃ©cnica**:
   - Contrastar contra el cÃ³digo fuente vigente. No asumir conteos, IDs, fechas o saldos histÃ³ricos como verdad absoluta sin verificar el estado actual del repositorio del consumer.
6. **Inmutabilidad histÃ³rica**:
   - No editar ni reescribir archivos de memorias histÃ³ricas ya existentes en `chats/`.

---

## Al finalizar una tarea

1. **Crear nueva memoria**:
   - Crear un archivo en `chats/YYYY-MM-DD-descripcion-tarea.md`.
   - Documentar: objetivo, cambios aplicados, archivos modificados, decisiones de diseÃ±o tomadas y consideraciones para tareas futuras.
2. **Actualizar `PROJECT_MEMORY.md`**:
   - Modificar Ãºnicamente si surge conocimiento transversal nuevo, un cambio arquitectÃ³nico o una conclusiÃ³n consolidada.
3. **Control de seguridad**:
   - Revisar exhaustivamente que ningÃºn archivo contenga contraseÃ±as, tokens, API keys o secretos de ningÃºn tipo.
4. **Commit y Push**:
   - Realizar commit y push exclusivamente de los archivos de documentaciÃ³n dentro del repositorio de contexto:
   ```bash
   git add .
   git commit -m "docs: registrar memoria de tarea <nombre-tarea>"
   git push origin main
   ```
5. **Reporte**:
   - Informar al usuario el archivo de memoria creado y el hash del commit generado.
