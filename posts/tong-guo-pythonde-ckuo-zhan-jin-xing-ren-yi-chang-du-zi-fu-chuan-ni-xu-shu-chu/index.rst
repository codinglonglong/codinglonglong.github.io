.. title: 通过Python的C扩展进行任意长度字符串逆序输出
.. slug: tong-guo-pythonde-ckuo-zhan-jin-xing-ren-yi-chang-du-zi-fu-chuan-ni-xu-shu-chu
.. date: 2015-09-07 12:42:48 UTC+08:00
.. tags: Python, C
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text

本文展示如何通过Python的C扩展进行任意长度字符串逆序输出。


1、编写C扩展stringreverse.c

.. code-block :: C
    :linenos:

    #include </usr/include/python3.4m/Python.h>

    static PyObject * StringError;  //错误信息对象
       
    // 自定义函数
    // 实现任意长度字符串反转
    int reverse(char * inputstr, int length, char * outputstr)
    {
      int i;
      for(i=length; i>0; i--)
        {
          outputstr[length-i] = inputstr[i-1];
        }
      outputstr[length] = '\0';
      return 1;
    }

    // Python和C的接口    
    static PyObject * stringreverse(PyObject * self, PyObject * args)
    {
      char * inputstr = NULL; // 用来接收参数的本地变量
      int length = 0;         // 用来接收参数的本地变量
      if (!PyArg_ParseTuple(args, "(si)", &inputstr, &length))  // 接收参数给本地变量
        return NULL;
      char *outputpointer = (char *) malloc(sizeof(char) * (length + 1)); // 分配返回值空间，多一位存放'\0'
      int sts;  // 判断函数是否成功执行
      sts = reverse(inputstr, length, outputpointer); // 调用自定义函数
      if (sts < 0) {
        PyErr_SetString(StringError, "Encode Error");
        return NULL;
      }
      return Py_BuildValue("s", outputpointer);  // 返回函数计算结果
    }

    // 声明方法调用接口
    static PyMethodDef StringReverseMethods[] = {
      {"reverse", stringreverse, METH_VARARGS,
       "Reverse A String."},  // {对外函数名称, 对内函数名称, 标志位, 函数说明}
      {NULL, NULL, 0, NULL}  //哨兵变量
    };
    /*
      METH_VARARGS标志位，用来告诉解释器应使用调用C函数的规则。
      当此位置为值0，表示PyArg_ParseTuple()函数使用的变量是废弃的。
      当仅使用时"METH_VARARGS"，表示希望参数经由PyArg_ParseTuple()被传递进来。
    */

    // 声明模块包含的方法集
    static struct PyModuleDef stringmodules = {
      PyModuleDef_HEAD_INIT,
      "stringreverse",
      NULL,
      -1,
      StringReverseMethods
    };

    // 模块初始化，包括异常处理
    PyMODINIT_FUNC PyInit_stringreverse(void)
    {
      PyObject *m;
      m = PyModule_Create(&stringmodules);
      if (m == NULL)
        return NULL;
      StringError = PyErr_NewException("stringreverse.error", NULL, NULL);
      Py_INCREF(StringError);
      PyModule_AddObject(m, "error", StringError);
      return m;
    }

    // 初始化
    void main(int argc, wchar_t *argv[])
    {
      PyImport_AppendInittab("stringreverse", PyInit_stringreverse);
      Py_SetProgramName(argv[0]);
      Py_Initialize();
      PyImport_ImportModule("stringreverse");
    }

    /*
      PyArg_ParseTuple()可以使用的格式参数
      "s" (string or Unicode object) [char *]
      "s#" (string, Unicode or any read buffer compatible object) [char *, int]
      "z" (string or None) [char *]
      "z#" (string or None or any read buffer compatible object) [char *, int]
      "u" (Unicode object) [Py_UNICODE *]
      "u#" (Unicode object) [Py_UNICODE *, int]
      "es" (string, Unicode object or character buffer compatible object) [const char *encoding, char **buffer]
      "es#" (string, Unicode object or character buffer compatible object) [const char *encoding, char **buffer, int *buffer_length]
      "b" (integer) [char]
      "h" (integer) [short int]
      "i" (integer) [int]
      "l" (integer) [long int]
      "c" (string of length 1) [char]
      "f" (float) [float]
      "d" (float) [double]
      "D" (complex) [Py_complex]
      "O" (object) [PyObject *]
      "O!" (object) [typeobject, PyObject *]
      "O&" (object) [converter, anything]
      "S" (string) [PyStringObject *]
      "U" (Unicode string) [PyUnicodeObject *]
      "t#" (read-only character buffer) [char *, int]
      "w" (read-write character buffer) [char *]
      "w#" (read-write character buffer) [char *, int]
      "(items)" (tuple) [matching-items]  ==> Py_BuildValue("(i, i)", 1, 2) (1, 2)
      "[items]" (list) [matching-items]   ==> Py_BuildValue("[i, i]", 1, 2) [1, 2]
      "{items}" (dictionary) [matching-items]  ==> Py_BuildValue("{s, i}", 'a', 2) {'a': 2}

      "|"
      Indicates that the remaining arguments in the Python argument list are optional. The C variables corresponding to optional arguments should be initialized to their default value -- when an optional argument is not specified, PyArg_ParseTuple() does not touch the contents of the corresponding C variable(s).
      ":"
      The list of format units ends here; the string after the colon is used as the function name in error messages (the ``associated value'' of the exception that PyArg_ParseTuple() raises).
      ";"
      The list of format units ends here; the string after the semicolon is used as the error message instead of the default error message. Clearly, ":" and ";" mutually exclude each other.
    */

2、将C扩展编译成动态链接库stringreverse.so
    
.. code-block :: Python
    :linenos:

    >> gcc -o stringreverse.so -shared -fPIC stringreverse.c


3、Python调用动态链接库test.py

.. code-block :: Python
    :linenos:

    import stringreverse
    aimstr = "abc"
    print(stringreverse.reverse((aimstr, len(aimstr))))

输出结果：

.. code-block :: Python
    :linenos:
   
    >> long@happytime:~/pythontest$ python3 test.py
    >> cba
    

