Estructura de un proyecto **Android Studio** en **Kotlin** siguiendo la arquitectura **MVVM**:

```
📂 MyApp/                      -> Carpeta principal del proyecto
├── 📂 .gradle/                -> Archivos temporales de Gradle
├── 📂 .idea/                  -> Configuración de Android Studio
├── 📂 app/                    -> Módulo principal de la app
│   ├── 📂 build/              -> Archivos generados automáticamente
│   ├── 📂 libs/               -> Librerías locales (.jar, .aar)
│   ├── 📂 src/                -> Código fuente
│   │   ├── 📂 main/           -> Código principal
│   │   │   ├── 📂 java/com/tuempresa/myapp/
│   │   │   │   ├── 📂 data/               -> Capa de datos (Model)
│   │   │   │   │    ├── 📂 model/         -> Modelos de datos (clases, DTO, entidades Room)
│   │   │   │   │    │    └── User.kt
│   │   │   │   │    ├── 📂 repository/    -> Lógica de negocio (acceso a datos)
│   │   │   │   │    │    └── UserRepository.kt
│   │   │   │   │    └── 📂 source/        -> Origen de datos (API, BD local)
│   │   │   │   │         ├── 📂 local/    -> Base de datos local (Room, SharedPreferences)
│   │   │   │   │         │    ├── AppDatabase.kt
│   │   │   │   │         │    └── UserDao.kt
│   │   │   │   │         └── 📂 remote/   -> Fuente de datos remota (API REST)
│   │   │   │   │              ├── ApiService.kt
│   │   │   │   │              └── ApiClient.kt
│   │   │   │   ├── 📂 ui/                 -> Capa de presentación (View)
│   │   │   │   │    ├── 📂 home/          -> Pantalla principal
│   │   │   │   │    │    ├── HomeActivity.kt
│   │   │   │   │    │    └── HomeFragment.kt
│   │   │   │   │    ├── 📂 login/         -> Pantalla de inicio de sesión
│   │   │   │   │    │    └── LoginFragment.kt
│   │   │   │   │    └── 📂 components/    -> Componentes reutilizables (botones, diálogos)
│   │   │   │   │         └── CustomButton.kt
│   │   │   │   ├── 📂 viewmodel/          -> Lógica de presentación (ViewModel)
│   │   │   │   │    ├── HomeViewModel.kt
│   │   │   │   │    └── LoginViewModel.kt
│   │   │   │   ├── 📂 di/                 -> Inyección de dependencias (Hilt/Dagger)
│   │   │   │   │    ├── AppModule.kt
│   │   │   │   │    └── NetworkModule.kt
│   │   │   │   ├── 📂 utils/              -> Utilidades y extensiones
│   │   │   │   │    ├── Extensions.kt
│   │   │   │   │    └── Constants.kt
│   │   │   │   └── 📂 navigation/         -> Navegación (Navigation Component)
│   │   │   │        └── AppNavigator.kt
│   │   │   ├── 📂 res/                    -> Recursos (XML)
│   │   │   │   ├── 📂 drawable/           -> Imágenes y formas vectoriales
│   │   │   │   ├── 📂 layout/             -> Archivos XML de vistas
│   │   │   │   ├── 📂 values/             -> Strings, colores, dimensiones
│   │   │   │   └── 📂 navigation/         -> Navigation Graph (nav_graph.xml)
│   │   │   └── AndroidManifest.xml       -> Declaración de componentes (Activity, permisos)
│   │   ├── 📂 test/                       -> Pruebas unitarias
│   │   └── 📂 androidTest/                -> Pruebas de UI (Espresso, UI Automator)
│   └── build.gradle.kts                  -> Configuración de Gradle (módulo app)
└── build.gradle.kts                      -> Configuración de Gradle (proyecto)
```

---

### 🧱 **Explicación de las carpetas principales:**

- **data/**

  - `model/`: Clases que representan tus datos (POJOs, DTOs, entidades de Room).
  - `repository/`: Fuente única de verdad (combina local y remoto).
  - `source/`: Fuentes de datos (local, remoto).

- **ui/**
  - Contiene las **Vistas (View)** como `Activity`, `Fragment` y componentes personalizados.
- **viewmodel/**

  - Aquí van los **ViewModel** que manejan la lógica de presentación y se comunican con el **Repository**.

- **di/**

  - Módulos para la **Inyección de Dependencias** (Dagger/Hilt).

- **utils/**

  - Funciones de utilidad, extensiones y constantes.

- **navigation/**
  - Controla la navegación de la aplicación usando **Navigation Component**.

---

### 📌 **Ejemplo de código en Kotlin (MVVM básico):**

✅ **`User.kt` (Modelo)**

```kotlin
data class User(
    val id: Int,
    val name: String,
    val email: String
)
```

✅ **`UserRepository.kt` (Repositorio)**

```kotlin
class UserRepository(private val api: ApiService) {
    suspend fun getUser(id: Int): User = api.getUserById(id)
}
```

✅ **`HomeViewModel.kt` (ViewModel)**

```kotlin
class HomeViewModel(private val repository: UserRepository) : ViewModel() {
    private val _user = MutableLiveData<User>()
    val user: LiveData<User> get() = _user

    fun fetchUser(id: Int) {
        viewModelScope.launch {
            _user.value = repository.getUser(id)
        }
    }
}
```

✅ **`HomeFragment.kt` (Vista)**

```kotlin
class HomeFragment : Fragment() {
    private val viewModel: HomeViewModel by viewModels()

    override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
        super.onViewCreated(view, savedInstanceState)

        viewModel.user.observe(viewLifecycleOwner) { user ->
            Log.d("User", "Usuario: ${user.name}")
        }

        viewModel.fetchUser(1)
    }
}
```
