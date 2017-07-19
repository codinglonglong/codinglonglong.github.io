.. title: Python命令行解析模块optparse
.. slug: pythonming-ling-xing-jie-xi-mo-kuai-optparse
.. date: 2015-09-08 11:08:18 UTC+08:00
.. tags: optparse, Python
.. category: 上学期间的文章
.. link: 
.. description: 
.. type: text


本文学习命令行参数解析的模块optparse。这个模块在Python2.7之后已经不鼓励使用，并由argparse所替代。

我们稍微改了一点Dpark中的源码如下opttest.py：

.. code-block :: python
    :linenos:
   
    import optparse
    
    parser = optparse.OptionParser(usage="Usage: %prog [options] [args]")
    # 禁用散置参数，参数解析到第一个非选项参数为止，之后的就不再作为选项解析
    parser.disable_interspersed_args()
    # 选项组
    group = optparse.OptionGroup(parser, "Dpark Options")
    group.add_option("-m", "--master", type="string", default="local",
                     help="master of Mesos: local, process, " +
                     "host[:port], or mesos: //")
    group.add_option("-p", "--parallel", type="int", default=0,
                     help="number of processes")
    group.add_option("-c", "--cpus", type="float", default=1.0,
                     help="cpus used per task")
    group.add_option("-M", "--mem", type="float", default=1000.0,
                     help="memory used per task")
    group.add_option("-g", "--group", type="string", default="",
                     help="which group of machines")
    group.add_option("--err", type="float", default=0.0,
                     help="acceptable ignored error record ratio (0.01%)")
    group.add_option("--snapshot_dir", type="string", default="",
                     help="shared dir to keep snapshot of RDDs")
    group.add_option("--conf", type="string",
                     help="path for configuration file")
    group.add_option("--self", action="store_true",
                     help="user self as exectuor")
    group.add_option("--profile", action="store_true",
                     help="do profiling")
    group.add_option("--keep-order", action="store_true",
                     help="deprecated, always keep order")
    parser.add_option_group(group)
    # 独立选项
    parser.add_option("-q", "--quiet", action="store_true")
    parser.add_option("-v", "--verbose", action="store_true")
    # 读取参数
    options, args = parser.parse_args()
    print(options)
    
我们执行代码:
::

   >> long@happytime:~/opttest$ python3 opttest.py 
   >> {'keep_order': None, 'self': None, 'group': '', 'parallel': 0, 'conf': None, 'snapshot_dir': '', 'cpus': 1.0, 'quiet': None, 'err': 0.0, 'master': 'local', 'mem': 1000.0, 'profile': None, 'verbose': None}
   >> long@happytime:~/opttest$ python3 opttest.py -p 10
   >> {'group': '', 'verbose': None, 'mem': 1000.0, 'self': None, 'conf': None, 'cpus': 1.0, 'keep_order': None, 'err': 0.0, 'quiet': None, 'snapshot_dir': '', 'profile': None, 'parallel': 10, 'master': 'local'}
   >> long@happytime:~/opttest$ python3 opttest.py -v
   >> {'snapshot_dir': '', 'conf': None, 'err': 0.0, 'self': None, 'profile': None, 'quiet': None, 'master': 'local', 'verbose': True, 'group': '', 'cpus': 1.0, 'parallel': 0, 'keep_order': None, 'mem': 1000.0}
   >> long@happytime:~/opttest$ python3 opttest.py --help
   >> Usage: opttest.py [options] [args]
   >> 
   >> Options:
   >>   -h, --help            show this help message and exit
   >>   -q, --quiet           
   >>   -v, --verbose         
   >> 
   >>   Dpark Options:
   >>     -m MASTER, --master=MASTER
   >>                         master of Mesos: local, process, host[:port], or
   >>                         mesos: //
   >>     -p PARALLEL, --parallel=PARALLEL
   >>                        number of processes
   >>     -c CPUS, --cpus=CPUS
   >>                         cpus used per task
   >>     -M MEM, --mem=MEM   memory used per task
   >>     -g GROUP, --group=GROUP
   >>                         which group of machines
   >>     --err=ERR           acceptable ignored error record ratio (0.01%)
   >>     --snapshot_dir=SNAPSHOT_DIR
   >>                         shared dir to keep snapshot of RDDs
   >>     --conf=CONF         path for configuration file
   >>     --self              user self as exectuor
   >>     --profile           do profiling
   >>     --keep-order        deprecated, always keep order

通过optparse，我们可以设定参数标识、参数默认值、参数类型和帮助信息等等内容。这样我们就可以让程序具有很强的适应性，最典型的应用就是Linux下各种命令行工具，强大的同时不失灵活。
