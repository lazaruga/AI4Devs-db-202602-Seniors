# Prompt del ejercicio DB

## 1) Traduccion de ERD a modelo Prisma
Convierte este ERD (Company, Employee, Position, InterviewFlow, InterviewStep, InterviewType, Candidate, Application, Interview) a `schema.prisma` para PostgreSQL. Manten compatibilidad con el modelo existente de Candidate/Education/WorkExperience/Resume y anade relaciones bidireccionales.

## 2) Normalizacion y buenas practicas
Propon mejoras de normalizacion sobre el ERD base: uso de enums para estados y tipos, restricciones de unicidad para evitar duplicados, y nombres de campos consistentes para claves foraneas.

## 3) Indices y rendimiento
Sugiere indices para todas las claves foraneas y para campos de consulta frecuente (`status`, `applicationDeadline`, `interviewDate`, `isActive`), justificando cada indice.

## 4) Migracion SQL con Prisma
Genera la migracion SQL equivalente al schema final mediante Prisma (`migrate diff` o `migrate dev`) para poder replicar la estructura en PostgreSQL.

## 5) Verificacion de estructura
Lista un checklist para validar en PGAdmin: comprobar tablas, FKs, indices, insertar datos de prueba y ejecutar consultas del flujo completo de seleccion.

## 6) Conexion de PGAdmin en Docker
Si PGAdmin tambien corre en Docker, indica la configuracion correcta para evitar errores de conexion:
- Host: `db` (nombre del servicio en `docker-compose.yml`)
- Port: `5432`
- Maintenance DB: `LTIdb`
- User: `LTIdbUser`
- Password: variable `DB_PASSWORD` del `.env`

Aclara que dentro del contenedor de PGAdmin no se debe usar `localhost` para conectar al contenedor de PostgreSQL.

## 7) Ajuste final detectado durante validacion
Incluye en el checklist final que, aunque la conexion a PGAdmin funcione, la BD puede aparecer vacia si no se ha aplicado la migracion.

Pasos de verificacion final:
1. Confirmar que hay tablas en `public` con:
   `SELECT tablename FROM pg_catalog.pg_tables WHERE schemaname = 'public' ORDER BY tablename;`
2. Si no hay tablas, ejecutar la migracion SQL de `backend/prisma/migrations/.../migration.sql`.
3. Refrescar `Databases > LTIdb > Schemas > public > Tables` en PGAdmin.
4. Repetir consulta de tablas y comprobar que aparecen las entidades del flujo completo.
