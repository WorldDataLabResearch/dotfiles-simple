#Tibble settings
options(tibble.print_max = 500)
options(tibble.print_min = 500)
options(tibble.width = Inf)

#Printing
options(max.print = 500) #Default is 99999

#X11
setHook(packageEvent("grDevices", "onLoad"),
  function(...) grDevices::X11.options(pointsize=30))

#Dont ask to save on quit()
utils::assignInNamespace(
  "q", 
  function(save = "no", status = 0, runLast = TRUE)
  {
    .Internal(quit(save, status, runLast))
  }, 
  "base"
)

utils::assignInNamespace(
  "quit", 
  function(save = "no", status = 0, runLast = TRUE) 
  {
    .Internal(quit(save, status, runLast))
  }, 
  "base"
)

#Save aliases, cant be deleted
.startup <- new.env()
assign("h", utils::head, env=.startup)
assign("n", base::names, env=.startup)
assign("s", base::summary, env=.startup)
assign("u", base::unique, env=.startup)
assign("d", base::dim, env=.startup)
assign("len", base::length, env=.startup)
assign("l", base::length, env=.startup)
assign("nas", function(df){sapply(df, function(x){sum(is.na(x))})}, env=.startup)
assign("infs", function(df){sapply(df, function(x){sum(is.infinite(x))})}, env=.startup)
assign("venn", function(a, b){list(a=a[!a %in% b], ab=intersect(a, b), b=b[!b %in% a])}, env=.startup)
assign("tab", function(...){base::table(..., useNA='ifany')}, env=.startup)
assign("int", function(a, b){intersect(names(a), names(b))}, env=.startup)
assign("dups", function(x){duplicated(x) | duplicated(x, fromLast=T)}, env=.startup)
assign("ihme_cols", c("#5e51a2", "#2f89be", "#66c3a6", "#add8a4", "#e4ea9a", "#fbf8c0", "#fce08a", "#faae61", "#f36c44", "#a01c44"), env=.startup)
assign("to_cmc", function(y, m){12*(y - 1900) + m}, env=.startup)
assign("from_cmc", function(cmc){
  y=1900 + floor((cmc - 1)/12)
  m=month.abb[cmc-12*(y-1900)]
  list(y, m)}, env=.startup)
assign("os", function(x){format(object.size(x), "auto")})
assign("unload.package", function(x){detach(paste0("package:", x), unload=TRUE)})
assign("debug_on", function(x){options(error=recover)})
assign("debug_off", function(x){options(error=NULL)})
attach(.startup)

#Show timestamp on Console
# .First <- function(){
#   h <- taskCallbackManager()
#   h$add(function(expr, value, ok, visible) { 
#     options("prompt"=format(Sys.time(), "%H:%M:%S> ")); 
#     return(TRUE) }, name = "simpleHandler")
# }

#Save history on exit
.Last <- function() {
  if (!any(commandArgs()=='--no-readline') && interactive()){
    require(utils)
    try(savehistory('~/.Rhistory'))
  }
}

# #Overload plus operator to work with strings like python
# "+" = function(x,y) {
#   if(is.character(x) || is.character(y)) {
#      return(paste(x , y, sep=""))
#   } 
#   if ("gg" %in% class(x)){
#     ggplot2:::`+.gg`(x, y)  
#   }else {
#      .Primitive("+")(x,y)
#   }
# }

