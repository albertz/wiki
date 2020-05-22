Experience KDevelop 5.5.0 (via Ubuntu 20.04), opening TensorFlow (1.15.2, Git checkout).
- Clicked open/import project, selected TF directory.
- Parsing takes very long.
- Does not find include files. Added custom include path.
- Parsing still takes very long (20 mins?).

Experience QtCreator 4.11.0 (via Ubuntu 20.04), opening TensorFlow (1.15.2, Git checkout).
- Import existing project by directory
- Parsing very fast (10 secs)
- Does not find include files.
  Needed to modify include paths (QtCreator .includes file).
  Removed all entries, just added `.`.
- Parsing again very fast (10 secs), now all seems fine.
- Some strange errors/crashes with clangbackend, but seems fine though.
