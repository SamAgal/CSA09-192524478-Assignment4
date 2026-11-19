# Java AWT & Swing Event-Driven Programming — Complete Solutions (Tasks 1–6)

## Repository Structure
- `src/task1/` — **Task 1.2**: Repaired Student Fee Payment GUI (`FeeWindow.java`, `FeeService.java`, `PaymentResult.java`) separating UI, validation, and JDBC persistence with non-blocking `SwingWorker`.
- `src/task2/` — **Task 2**: Hospital Outpatient Appointment Desk (`OutpatientAppointmentFrame.java`) with `Map<String, List<String>>` department-doctor cache, validation, and window-close confirmation guard.
- `src/task3/` — **Task 3.3**: Campus Library Search Screen (`LibrarySearchScreen.java`) implemented in AWT using nested `BorderLayout` + `GridLayout` + `FlowLayout` containers.
- `src/task4/` — **Task 4.3**: Repaired Drawing Pad (`DrawPad.java`) storing click coordinates in `ArrayList<Point>` and redrawing them in `paint(Graphics g)`.
- `src/task5/v1/` — **Task 5.1**: Currency Converter implemented in four event-handling styles (`ConverterStyleA.java`, `ConverterStyleB.java`, `ConverterStyleC.java`, and `Converter.java` lambda version).
- `src/task5/v2/` — **Task 5.2**: Modified Currency Converters supporting `Enter` key submission and `JOptionPane` result dialogs.
- `src/task6/` — **Task 6**: Layered Campus Event Registration Desktop Application (`Registration.java`, `DatabaseConfig.java`, `RegistrationDAO.java`, `RegistrationService.java`, `EventRegistrationFrame.java`, `EventRegistrationApp.java`).
- `sql/campus_events.sql` — MySQL DDL schema (`UNIQUE(student_id, event_name)`), composite index, and sample seed data for Task 6.
- `screenshots/` — Output screenshots linked to every tested requirement and interaction.

## Compilation & Execution
```bash
# Compile all tasks (ensure MySQL Connector/J is on classpath for Task 1 and Task 6)
javac -d out src/task1/*.java src/task2/*.java src/task3/*.java src/task4/*.java src/task5/v1/*.java src/task5/v2/*.java src/task6/*.java

# Run individual tasks
java -cp out task1.FeeWindow
java -cp out task2.OutpatientAppointmentFrame
java -cp out task3.LibrarySearchScreen
java -cp out task4.DrawPad
java -cp out task5.v1.Converter
java -cp "out:mysql-connector-j.jar" task6.EventRegistrationApp
```

## Linked Test Evidence Matrix
| Screenshot File | Task / Requirement | Demonstrated Test Case |
| :--- | :--- | :--- |
| `screenshots/task1_fee_payment_success.png` | Task 1.2 | Valid payment processed asynchronously via `FeeService` + Receipt modal |
| `screenshots/task1_fee_validation_error.png` | Task 1.2 | Invalid/non-numeric amount rejected cleanly without freezing EDT |
| `screenshots/task2_outpatient_booking.png` | Task 2.1–2.3 | Dynamic doctor list refresh on department change + Appointment confirmation |
| `screenshots/task2_close_confirmation.png` | Task 2.4 | `WindowAdapter.windowClosing` prompt when booking is in progress |
| `screenshots/task3_library_initial.png` | Task 3.3 | Initial library search layout (`650 x 420`) with search & pagination |
| `screenshots/task3_library_resized.png` | Task 3.4 | Resized window (`920 x 580`) proving `CENTER` results expand while controls keep size |
| `screenshots/task4_drawpad_before_minimize.png` | Task 4.3 | Repaired `DrawPad` displaying 6 clicked dots and `"Clicks: 6"` |
| `screenshots/task4_drawpad_after_restore.png` | Task 4.3 | Restored `DrawPad` after minimize proving dots survive `paint()` |
| `screenshots/task4_override_compiler_error.png` | Task 4.4 | `javac` compile-time error when `@Override` is placed on misspelled `mouseclicked` |
| `screenshots/task5_converter_valid_and_invalid.png` | Task 5.1 & 5.2 | Valid conversion (`12.00 USD`), `"Invalid amount"` handling, and `JOptionPane` dialog |
| `screenshots/task6_event_reg_normal_and_filter.png` | Task 6 Stage 5 | Normal registration + paginated `JTable` filtered by `Hackathon 2026` |
| `screenshots/task6_event_reg_invalid_and_duplicate.png` | Task 6 Stage 5 | Rejection of invalid student ID and duplicate `(student_id, event_name)` |
