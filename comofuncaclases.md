# CLASS.CPP

INTRUCCIONES Y VERSIONES

Version 1.0: añadiendo las primeras clases

-se añadieron las primeras clases base.

Como usar las clases, descripcion de cada una

    1.- elemento
    
    clase compuesta por una variable string, representa un atributo elemental del supuesto rpg, tiene 
    funciones para obtener su valor para setear, su constructor requiere una variable de tipo string
    
    atributos privados: string nombre; 
    
    elemento(string)
    
    funciones:
    
    set_elemento(string) .- para modificar el string del elemento
    getnombre() .- funcion que retorna solamente el string que lo conforma
    
    2.- rama_elemental
    
    clase que conforma una lista de elementos, y ademas genera una tabla de debilidades mediante un 
    arreglo bidimensional, su constructor solo admite el numero maximo de elementos a obtener
    
    atributos privados: elemento *lista, int **tabla_debilidades, int numero
    
    rama_elemental(int)
    
    funciones:
    
    set_element(int, string) .- funcion que llama a la funcion set_elemento de la clase elemento, para 
    fijar un nombre a un elemento del arreglo de elementos, int pide la posición en el arreglo, mientras
    que string pide un nombre
    
    void set_debilidad_fortaleza (string, string, string).- fija relaciones de debilidad y fortaleza en el arreglo 
    bidimensional tabla_debilidades, el primer string pide el nombre del elemento a fijar, el segundo pide el 
    nombre del elemento el cual es debil, y el tercero pide el nombre del elemento el cual es fuerte, esto modifica
    el arreglo bidimensional mediante numeros, 1 si no es fuerte o debil, 2 si es fuerte, 0 si es debil, y 3 si
    es fuerte y debil a la vez (ADVERTENCIA: SE SOLICITA CAMBIAR EL ARREGLO BIDIMENSIONAL POR UNA RELACION LOGICA
    COMO GRAFOS)
    
    string get_nombre(int) devuelve el nombre del elemento el la posicion int
    
    void mostrar tabla() imprime el arreglo bidimensional mostrando las debilidades representadas por los numeros
    
    3.-Estadistica
    
    Clase que representa una estadistica tipica de un personaje en rpgs, por ejemplo ataque, defensa entre otros
    sus atributos son un valor int y un nombre string, posee un constructor por defecto, otro insertando datos
    y un constructor copia
    
    atributos privados: string nombre, int valor
    
    estadistica(string, int)
    
    funciones.-
    
    int get_valor() string get_nombre() .- retornan ambas estadisticas cada uno
    
    void set_valor(int) void set_nombre(string) .- permite modificar ambos valores
    
    void sumar valor(int) .- establece el valor como la suma de este y la variable int que pide el proceso
    
    4.-stats
    
    Clase que almacena una lista de estadisticas, esta puede ser usada para los atributos de un personaje
    tiene un constructor por defecto, otro insertado datos y un constructor copia
    
    atributos privados.- estadistica *S, int tamano
    
    stats(int, string[], int[]).- pide una variable para establecer el tamaño del arreglo, la lista de string 
    e int pide los nombres de las estadisticas, los elementos de una misma posición llamaran al constructor 
    de estadistica para crear la lista de estadisticas
    
    
    atributos privados: estadistica *S, int tamano
    
    funciones.-
    
    int get_tamano().- para devolver la variable tamano
    int get_stats_valor(int) .- llama a las funcion get_valor de la estadistica en el arreglo S, int pide su posicion
    int get_stat_nombre(int).- llama a la funcion get_nombre de la estadsitica en el arreglo S, in pide su posicion
    void mostrar_stats().- muestra los atributos en orden del arreglo S
    
    5.- nivel
    
    Clase que establece el caracterisitco nivel que representa la fuerza de nuestro personaje, este aporta herramientas
    basicas para cumplir las funciones que tiene un sistema asi, posee los tres tipos de constructores
    
    atributos .- double nive, experiencia, exp_necesaria, nivel_maximo, constante
    
    nive: representa el nivel actual
    experiencia: representa la experiencia parcial para subir al siguiente nivel,
    exp_necesaria: representa la experiencia que se necesita para subir de nivel
    exp_total: representa la experiencia total que a recaudado el personaje
    nivel_maximo: el nivel maximo al que se puede llegar
    constante: valor por el cual representara el numero que se elevará exponencialmente, su valor por defecto es e
    
    nivel(double,double,double,double,double,double) (todos representan los atributos de arriba)
    
    funciones.-
    
    double getexptotal() retorna exp_total
    double getnivel() retorna nive
    double getexp() retorna experiencia
    double getexpn() retorna exp_necesaria
    double getnivel_max() retorna nivel_maximo
    double get_constante() retorna constante
    
    void set_exnec().- setea la experiencia necesaria mediante la formula: (constante ^ (nive/10))*100
    void aumentar_exp(double) .- suma los valores experiencia y exp_total por la variable double
    void subir_nivel(double) .- proceso mediante el cual se sube de nivel, experiencia toma el valor de double
                                nive aumenta siempre que sea menor al nivel_maximo, y se llama al proceso
                                set_exnec para fijar la nueva exp_necesaria para volver a subir de nivel
    void sistema_de_validacion .- basicamente compara la experiencia con exp_necesaria para validar si subir de nivel 
                                  o no, llama a la funcion subir_nivel e introduce la diferencia entre experiencia
                                  y exp_necesaria
                                  
    6.- estado
    
    clase que representa un estado alterado de un persoanje
    
    atributos: string nombre, codigo_efecto
    
    estado(string, string)
    
    funciones.-
    
    void set_nombre(string) void set_codigo(string) funciones para fijar los atributos del estado
    string getnombre() string get_codigo() funciones para retornar los atributos
    
    7.- Habilidad
    
    clase que representa una habilidad que puede ser usada en un hipotetico combate, por ahora solo
    se enfoca en habilidades ofensivas
    
    atributos: string nombre, int potencia, elemento elem, estado stad
    
    habilidad(string, int, rama_elemental, int, string, string){
        nombre = x;
        potencia = y;
        elem.set_elemento(z.get_nombre(zx));
        stad.setnombre(r);
        stad.set_codigo(k);}
        
    funciones: 
    
    string get_nombre .- muestra nombre
    int get_potencia .- muestra potencia
    string get_elemento .- muestra nombre del elemento elem
    string get_estado -.- muestra nombre del estado stas
    
    void set_nombre(string) void set_potencia(int).- establece el nombre y potencia
    void set_elemento(rama_elemental, int) .-establece el elemento llamando a una rama_elemental existente
                                            y la posicion del elemento deseado
    void set_estado(estado) .- establece el nombre y codigo_efecto usando el elemento de entrada
    
    void mostrar_datos() .- muestra los datos de la habilidad usando sus funciones get
    
    8.- item
    
    funcion padre que representa todo tipo de objeto
    
    atributos protegidos: string name, string description
    
    item(string, string)
    
    funciones:
    
    string get_nombre() string get_description() retorna name y descrption respectivamente
    void set_nombre(string) void set_descriptcion(string) establece valores para name y descrption
    
    9.- tipo_de_arma
    
    funcion que establece un tipo de arma usada para dañar
    
    atributos: string tipo
    
    tipo_de_arma(string)
    
    funciones:
    
    void set_tipo(string).- establece tipo
    int get_tipo().- retorna tipo
    
    10.- weapon:item
    
    clase basada en item que representa un arma real del juego, posee dos arreglos de string e int
    que representa los stats modificados por el arma ademas de el aumento/decremento
    
    atributos: int tamano, string *stat_mejorado, int *aumento, elemento element, tipo_de_arma typ
    
    weapon(int x)
    {
        item();
        tip = tipo_de_arma();
        stat_mejorado = new string[x];
        aumento = new int[x];
        tamano = x;
        element=elemento();
    }
    weapon (string descr, string x, string y[],int f, int z[], string elem, tipo_de_arma typ)
    {
        set_nombre(x);
        set_descripcion(descr);
        tamano = f;
        stat_mejorado = new string[f];
        for(int i = 0; i < tamano; i++)
            stat_mejorado[i]=y[i];
        aumento = new int[f];
        for(int i = 0; i < tamano; i++)
            aumento[i]=z[i];
        element = elemento(elem);
        tip = tipo_de_arma(typ.get_tipo());
    }
    
    funciones: 
    
    string description() retorna a la función get_description() heredada de item
    int get_tamano() retorna tamano,
    string nombre() retorna a la funcion get_nombre() heredada de item
    string get_stat_mejorado(int) retorna un elemento de la lista stat_mejorado en la posicion int
    int get_aumento(int) retorna un elemento de la lista aumento en posicion int
    string get_elemento() retorna la variable nombre del atributo elemento element
    void set_stats_mejorados_plus_stat_(string[], int[]) establece nombre de estadisticas aumentadas
                                                         con su respectivo aumento
    void set_elemento(elemento) establece el nombre del atributo element del nombre de una variable
                                elemento
    
    void mostrar_datos() muestra todos los datos del objeto weapon
    
    11.-  clase
    
    representa un conjunto de caracteristicas especificas para la creacion de personajes, es la base
    para crear roles como mago, guerrero, clerigo, etc.
    
    atributos: string nombre, int tam, habilidad *H, int *niveles_para_llegar, string beneficio_stats, strin beneficio_armas
    
    clase(int x)
    {
        nombre = "vacio";
        tam = x;
        for(int i=0;i<tam;i++)
            H[i]=new habilidad;
        for(int j=0;j<tam;j++)
            niveles_para_llegar[j]=new int;
        beneficio_stats="0000000";
        beneficio_armas="xxxxxxx";
    }
    
    funciones
    
    void nombrar(string) establece la variable nombre
    void setear_stats(string) establece beneficio_stats
    void setear_armas(string) establece beneficio_armas
    void set_habilidades(int,int,string,rama_elemental, int, estado)
    crea una habilidad en la lista de habilidad, a su vez establece un numero a *niveles para llegar
    (int o, int niv,string x, int y, rama_elemental z, int zx, estado cf)
    {
        H[o]->set_nombre(x);
        H[o]->set_potencia(y);
        H[o]->set_elemento(z,zx);
        H[o]->set_estado(cf);
        *niveles_para_llegar[o]=niv;
    }  
   void mostrar_datos() muestra con detalle los atributos del objeto
  
