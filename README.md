# 📸 Modelo de Base de Datos para Instagram

Este proyecto consiste en la creación de un modelo de base de datos para Instagram utilizando **SQLAlchemy** en Python. El objetivo es replicar la estructura de datos de una red social similar a Instagram, permitiendo almacenar información sobre usuarios, publicaciones, comentarios, medios y seguidores.

---

## 🌱 Cómo iniciar este proyecto

Para comenzar con este proyecto, es necesario hacer un **fork** del [repositorio original](https://github.com/breatheco-de/exercise-instagram-data-modeling) en tu cuenta de **GitHub** y luego clonarlo en tu entorno local o abrirlo en **Gitpod**.

Dentro del archivo `src/models.py` encontrarás la estructura base de SQLAlchemy, que deberás modificar para replicar la base de datos de Instagram.

Aquí hay un video que explica qué es UML: [Ver video](https://www.youtube.com/watch?v=UI6lqHOVHic)

---

## 📊 Diagrama de la Base de Datos

Este proyecto genera un **Diagrama de Relaciones de Entidad (ERD)** que representa la estructura de datos de Instagram. Se incluyen entidades como **Usuario, Post, Comentario, Media y Follower**, junto con sus respectivas relaciones.

Puedes visualizar un diagrama similar al que se generará con este proyecto en el siguiente enlace: [Diagrama ERD de ejemplo](https://app.quickdatabasediagrams.com/#/d/LxNXQZ)

> 🔥 También puedes practicar diagramación con esta herramienta GRATUITA: [Quick Database Diagrams](https://app.quickdatabasediagrams.com/#/d/)

---

## 💻 Instalación

Para ejecutar el proyecto en tu entorno local, sigue estos pasos:

1. Activa el entorno virtual:  
   ```bash
   $ pipenv shell
   ```
2. Instala las dependencias necesarias:  
   ```bash
   $ pipenv install
   ```
3. Genera el diagrama UML ejecutando el siguiente comando:  
   ```bash
   $ python src/models.py
   ```
4. Abre el archivo `diagram.png` para visualizar el modelo generado.

---

## 📝 Instrucciones

El objetivo principal de este proyecto es completar el archivo `src/models.py` para replicar la base de datos de Instagram utilizando **SQLAlchemy**. Asegúrate de incluir:

✅ **Mínimo 4 modelos** con todas sus propiedades y relaciones.  
✅ **Definir correctamente las claves primarias y foráneas**.  
✅ **Actualizar el archivo `diagram.png`** generando nuevamente el diagrama después de modificar los modelos.  
✅ **Utilizar SQLAlchemy y la herramienta ERAlchemy2** para visualizar el modelo.

Las tablas incluidas en el modelo de datos son:

1. **User** → Almacena la información de los usuarios.
2. **Post** → Contiene los posts creados por los usuarios.
3. **Comment** → Registra los comentarios en las publicaciones.
4. **Media** → Almacena imágenes y videos asociados a los posts.
5. **Follower** → Representa la relación de seguidores entre usuarios.

Cada modelo tiene las propiedades necesarias para replicar el comportamiento de Instagram.

---

## 🚀 Descripción de Modelos

### **User (Usuario)**
Guarda la información de los usuarios registrados en la plataforma.
```python
class User(Base):
    __tablename__ = 'user'
    id = Column(Integer, primary_key=True)
    username = Column(String(50), unique=True, nullable=False)
    firstname = Column(String(50), nullable=False)
    lastname = Column(String(50), nullable=False)
    email = Column(String(100), unique=True, nullable=False)
```

### **Post (Publicación)**
Almacena las publicaciones realizadas por los usuarios.
```python
class Post(Base):
    __tablename__ = 'post'
    id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('user.id'), nullable=False)
```

### **Comment (Comentario)**
Representa los comentarios realizados en las publicaciones.
```python
class Comment(Base):
    __tablename__ = 'comment'
    id = Column(Integer, primary_key=True)
    comment_text = Column(String(255), nullable=False)
    author_id = Column(Integer, ForeignKey('user.id'), nullable=False)
    post_id = Column(Integer, ForeignKey('post.id'), nullable=False)
```

### **Media (Multimedia)**
Contiene imágenes y videos asociados a los posts.
```python
class Media(Base):
    __tablename__ = 'media'
    id = Column(Integer, primary_key=True)
    type = Column(Enum('image', 'video', name='media_types'), nullable=False)
    url = Column(String(255), nullable=False)
    post_id = Column(Integer, ForeignKey('post.id'), nullable=False)
```

### **Follower (Seguidores)**
Representa la relación entre seguidores y seguidos.
```python
class Follower(Base):
    __tablename__ = 'follower'
    user_from_id = Column(Integer, ForeignKey('user.id'), primary_key=True)
    user_to_id = Column(Integer, ForeignKey('user.id'), primary_key=True)
```

---

## 📷 Generación del Diagrama

Una vez definidos los modelos en `src/models.py`, ejecuta:
```bash
$ python src/models.py
```
Esto generará el archivo `diagram.png` con la estructura de la base de datos.

---

## 📚 Recursos Adicionales

- [Documentación de SQLAlchemy](https://docs.sqlalchemy.org/)
- [Uso de ERAlchemy2](https://github.com/AlexisMN/eralchemy2)
- [Ejemplo de diagramas UML](https://app.quickdatabasediagrams.com/)

Este proyecto es parte de la formación en desarrollo de software de [4Geeks Academy](https://4geeksacademy.com/), enseñando a programadores a modelar bases de datos de manera efectiva.

¡Diviértete construyendo tu base de datos para Instagram! 🚀

## 👨‍💻 **Autor**

- **Desarrollado por JulioRom**
- 📧 **Correo:** [julioandrescampos@gmail.com](mailto:julioandrescampos@gmail.com)
- 🔗 **GitHub:** [https://github.com/JulioRom](https://github.com/JulioRom)
