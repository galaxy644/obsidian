struct IntArray2d{

int & get(size_t i,size_t j){

return data[i*b+j];

}

size_t a;

size_t b;

int* data;

};