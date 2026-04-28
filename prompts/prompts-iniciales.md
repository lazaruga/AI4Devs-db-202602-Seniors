# Prompts iniciales del ejercicio DB

## 1) Traduccion de ERD a modelo Prisma
Convierte este ERD (Company, Employee, Position, InterviewFlow, InterviewStep, InterviewType, Candidate, Application, Interview) a `schema.prisma` para PostgreSQL. Manten compatibilidad con el modelo existente de Candidate/Education/WorkExperience/Resume y anade relaciones bidireccionales.

## 2) Normalizacion y buenas practicas
Propone mejoras de normalizacion sobre el ERD base: uso de enums para estados y tipos, restricciones de unicidad para evitar duplicados, y nombres de campos consistentes para claves foraneas.

## 3) Indices y rendimiento
Sugiere indices para todas las claves foraneas y para campos de consulta frecuente (`status`, `applicationDeadline`, `interviewDate`, `isActive`), justificando cada indice.

## 4) Migracion SQL con Prisma
Genera la migracion SQL equivalente al schema final mediante Prisma (`migrate diff` o `migrate dev`) para poder replicar la estructura en PostgreSQL.

## 5) Verificacion de estructura
Lista un checklist para validar en PGAdmin: comprobar tablas, FKs, indices, insertar datos de prueba y ejecutar consultas del flujo completo de seleccion.
