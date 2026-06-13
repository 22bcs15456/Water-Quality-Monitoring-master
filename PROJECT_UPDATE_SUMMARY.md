# Java Upgrade Summary: Water Quality Monitoring Backend

- Session ID: `20260613093604`
- Date: 2026-06-13
- Target: Java 21 LTS
- Status: Successfully completed and verified

## Changes

- The Maven build targets Java 21 through `<java.version>21</java.version>`.
- Spring Boot remains on 3.3.0, which supports Java 21.
- Tests run with an isolated H2 in-memory database through the `test` profile.
- GitHub Actions verifies the backend with Eclipse Temurin Java 21.
- The README documents Java 21 as a project requirement and includes backend run commands.

## Verification

The backend was verified on 2026-06-13 using Eclipse Temurin 21.0.11:

```powershell
cd backend
$env:JAVA_HOME='<path-to-jdk-21>'
.\mvnw.cmd clean verify
```

Result:

- Maven build: passed
- Java compiler target: `release 21`
- Production sources compiled: 10
- Test sources compiled: 1
- Tests: 1 passed, 0 failed, 0 errors, 0 skipped
- Spring Boot executable JAR: created successfully

No application source changes were required for Java 21 compatibility.

## Runtime Configuration

The production profile expects MySQL using the settings in `backend/src/main/resources/application.properties`. Credentials should be supplied through environment-specific configuration before deployment rather than committed production secrets.

The developer machine may have another Java version first on `PATH`. Set `JAVA_HOME` to a Java 21 JDK before running the backend locally.
