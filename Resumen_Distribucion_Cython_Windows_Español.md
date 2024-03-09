
Resumen de Pasos para la Distribución de un Programa Cython en Windows
-----------------------------------------------------------------------

1. **Renombrar y preparar**:
   - Cambia el nombre de `max.py` a `max.pyx`.

2. **Instalar Cython**:
   - Ejecuta `pip install Cython`.

3. **Instalar un compilador C/C++**:
   - Asegúrate de tener Microsoft C++ Build Tools instalado.

4. **Crear `setup.py`**:
    ```
    from setuptools import setup
    from Cython.Build import cythonize

    setup(
        ext_modules=cythonize("max.pyx")
    )
    ```

5. **Compilar a binario**:
   - Ejecuta `python setup.py build_ext --inplace` para generar `max.pyd`.

6. **Empaquetar la aplicación** (opcional):
   - Instalar PyInstaller: `pip install pyinstaller`.
   - Crear ejecutable: `pyinstaller --onefile tu_script_principal.py`.

7. **Estructura de directorio para distribución** (sin `.pyx`):
    ```
    MiAplicacion/
    ├── dist/                  # Ejecutable PyInstaller (si aplicable)
    │   └── MiAplicacion.exe   
    ├── bin/                   # Binarios de Cython (`.pyd`)
    │   └── max.pyd            
    ├── lib/                   # Dependencias adicionales (si las hay)
    ├── requirements.txt       # Dependencias Python (si no está todo empaquetado)
    └── README.md              # Instrucciones de instalación y uso
    ```

8. **Distribuir**:
   - Entrega la carpeta `MiAplicacion/` a tus usuarios finales.
