# Doxygen

Doxygen is an open-source documentation generator. It extracts specially formatted comments from source code and creates reference documentation for functions, classes, files, and modules. It supports languages including C, C++, Java, and Python.

## 1. Install and check

- **Windows:** download the installer from https://www.doxygen.nl/download.html
- **macOS:** `brew install doxygen`
- **Debian/Ubuntu:** `sudo apt-get install doxygen`
- Check installation: `doxygen --version`

## 2. Basic workflow

```bash
doxygen -g Doxyfile   # Generate a configuration template
doxygen Doxyfile      # Generate documentation
```

1. Write documentation comments in source files.
2. Create or edit `Doxyfile`.
3. Set input paths and output formats.
4. Run Doxygen.
5. Open `html/index.html` to browse the generated documentation.

## 3. C/C++ comment syntax

Doxygen recognizes special comment formats such as `/** ... */` and `///`.

```cpp
/**
 * @brief Returns the sum of two integers.
 * @param a First integer.
 * @param b Second integer.
 * @return Sum of a and b.
 */
int add(int a, int b);
```

## 4. Tags shown in the lecture

| Tag | Meaning |
|---|---|
| `\\brief` or `@brief` | Short summary of a function, class, or module |
| `\\param` or `@param` | Description of a parameter |
| `\\return` or `@return` | Description of return value |
| `\\author` or `@author` | Author information |
| `\\version` or `@version` | Version information |
| `\\see` or `@see` | Reference to related items |
| `\\note` or `@note` | Additional note |
| `\\class` or `@class` | Documents a class |
| `@file` | Documents a source/header file |

Class example:

```cpp
/**
 * @class Car
 * @brief Represents a car object.
 */
class Car {
public:
    /**
     * @brief Starts the engine.
     * @return True if starting succeeds.
     */
    bool startEngine();
};
```

## 5. Python docstring example

The lecture also shows Python-style documentation fields:

```python
def foo(bar: int) -> int:
    """
    Brief description.
    More details here.

    :param bar: Bar parameter
    :type bar: int
    :return: Computed value
    :rtype: int
    """
    return bar + 1
```

## 6. Doxyfile settings

| Setting | Purpose |
|---|---|
| `PROJECT_NAME` | Project name shown in output |
| `INPUT` | Files or directories to document |
| `RECURSIVE = YES` | Scan subdirectories |
| `EXTRACT_ALL = YES` | Include entities even without comments |
| `GENERATE_HTML = YES` | Generate HTML pages |
| `GENERATE_LATEX = YES` | Generate LaTeX output |
| `GENERATE_RTF = NO` | Disable RTF output |
| `GENERATE_XML = NO` | Disable XML output |
| `HAVE_DOT = YES` | Enable Graphviz diagrams when installed |

Doxygen can produce HTML, LaTeX/PDF, RTF, XML, DocBook, and man pages.

## 7. Diagrams and grouping

The slides introduce Graphviz integration (`HAVE_DOT = YES`), `@dot` blocks, PlantUML directives, logical grouping, and Markdown/HTML tables and images inside documentation.

## 8. Best practices

- Explain the purpose and behaviour of an API, not merely its name.
- Keep brief summaries separate from longer descriptions.
- Document public functions, classes, and modules.
- Use consistent tags and comment style.
- Store `Doxyfile` with the source code and update docs during code reviews.
- Generated documentation can be published using GitHub Pages or an internal documentation site.

Write useful comments in code, configure Doxygen, and regenerate the documentation when the code changes.
