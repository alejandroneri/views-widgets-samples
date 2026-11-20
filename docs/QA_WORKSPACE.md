# Política de QA-Workspace — views-widgets-samples

**Ámbito:** este repositorio y cualquier agente o persona que cree checkouts, informes, capturas, análisis, ZIP o evidencias locales. Vigente para nuevas actividades; no autoriza limpieza, publicaciones, cambios funcionales ni datos reales.

## Raíz obligatoria en Windows

`$HOME\QA-Workspace\Ejemplos\repos\views-widgets-samples`.

```text
QA-Workspace/
  Ejemplos/
    repos/
      views-widgets-samples/
        checkouts/
          PR-NNN-SHA12/
        evidencias/
          PR-NNN/
            AAAAMMDD-HHMMSS-SHA12-ID/
              metadata.json
              resultados.json
              tests.log
              git-status.txt
        comparaciones/
          PR-NNN-vs-main/
```

## Reglas para agentes y ejecutores

1. Antes de dar comandos de PowerShell, leer `AGENTS.md` y esta política, comprobar el repositorio y su rama principal `main` contra GitHub, y fijar PR, rama y SHA.
2. Crear un checkout nuevo por candidato bajo `checkouts/`. Verificar `git rev-parse HEAD` y `git status --short` antes de reusar. Prohibido sobrescribir cambios existentes mediante `reset --hard`, `git clean`, `pull` o eliminación automática.
3. Cada ejecución tiene una carpeta única en `evidencias/PR-NNN/`: guardar datos de identificación, versiones y comando en `metadata.json`, códigos de salida y estados `PASS_LOCAL`, `FAIL`, `BLOQUEADO` o `NO_EJECUTADO` en `resultados.json`, y logs/capturas/ZIP dentro de la misma carpeta.
4. Comparaciones contra la rama principal utilizan otro checkout, su SHA explícito y registros en `comparaciones/`. Nunca confundir existencia de pruebas con PASS.
5. **No crear nuevos archivos de QA** en `$HOME`, `Downloads`, `Desktop`, `$env:TEMP` ni la raíz del repositorio. Solo se admiten cachés y artefactos automáticos de la herramienta dentro de un checkout, y sin versionar.
6. Conservar íntegros los checkouts y las evidencias históricas dispersas. Inventariar antes de copiar o trasladar; nunca mover, borrar, limpiar o reescribir históricos sin autorización expresa.

No guardar ni publicar secretos, identificadores personales, finanzas ni datos de producción en evidencias. El workspace físico del PC **no se crea ni verifica por la presencia de esta documentación**. Esta política no activa procesos de QA, CI, deploy ni migraciones.
