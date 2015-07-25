# Programming-R
makeCacheMatrix <- function(x = matrix()) {
cachedInverse <- NULL
set <- function(y) {
x <<- y
cachedInverse <<- NULL
}
get <- function() x
setInverse <- function(inverse) cachedInverse <<- inverse
getInverse <- function() cachedInverse
list(set = set, get = get,
setInverse = setInverse,
getInverse = getInverse)
}
##return the matrix that is the inverse of "x"
cacheSolve <- function(x, ...) {
invFunc <- x$getInverse()
if(!is.null(invFunc)) {
message("getting cached data")
return(invFunc)
}
data <- x$get()
invFunc <- solve(data, ...)
x$setInverse(invFunc)
invFunc
}
