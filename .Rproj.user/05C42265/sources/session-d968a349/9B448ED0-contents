build_and_publish <- function(mensaje = NULL) {
  if (!requireNamespace("bookdown", quietly = TRUE)) {
    stop("El paquete 'bookdown' no está instalado.")
  }
  
  if (is.null(mensaje) || mensaje == "") {
    mensaje <- paste("Actualización del libro:", Sys.time())
  }
  
  cat("1. Compilando libro...\n")
  bookdown::render_book("index.Rmd")
  
  cat("2. Agregando archivos a Git...\n")
  system("git add .")
  
  cat("3. Creando commit...\n")
  commit_cmd <- paste0('git commit -m "', mensaje, '"')
  commit_status <- system(commit_cmd)
  
  if (commit_status != 0) {
    cat("Aviso: no se creó un nuevo commit. Puede que no haya cambios para guardar.\n")
  }
  
  cat("4. Enviando cambios a GitHub...\n")
  system("git push")
  
  cat("Proceso finalizado.\n")
}