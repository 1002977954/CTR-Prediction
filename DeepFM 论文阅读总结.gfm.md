
## Abstract

Learning sophisticated feature interactions behind user behaviors is critical in maximizing CTR for recommender systems. Despite great progress, existing methods seem to have a strong bias towards low- or high-order interactions, or require expertise feature engineering. In this paper, we show that it is possible to derive an end-to-end learning model that emphasizes both low- and highorder feature interactions. The proposed model, DeepFM, combines the power of factorization machines for recommendation and deep learning for feature learning in a new neural network architecture. Compared to the latest Wide & Deep model from Google, DeepFM has a shared input to its ��wide�� and ��deep�� parts, with no need of feature engineering besides raw features. Comprehensive experiments are conducted to demonstrate the effectiveness and efficiency of DeepFM over the existing models for CTR prediction, on both benchmark data and  commercial data.

## 1. CTRԤ��

CTRԤ�� **�����ص�** ��

1. �����а�������ͺ����������ݡ������������Ҫone-hot,���������ݿ�������ɢ����one-hot��Ҳ����ֱ�ӱ���ԭֵ
2. ά�ȷǳ���
3. ���ݷǳ�ϡ��
4. ��������Field����

CTRԤ�� **�ص�** ����**ѧϰ�������**��ע�⣬��������������ס������������߽׵ģ�����Խ��Խ���ӣ�Խ������ѧϰ��Google�������о��ó����ۣ��߽׺͵ͽ׵�����������ǳ���Ҫ��ͬʱѧϰ���������������������Ҫ��ֻ��������һ�ֵ�����Ҫ�á�

��ô�ؼ�����ת���ɣ� **��θ�Ч����ȡ��Щ�������** ��һ�ְ취������������֪ʶ�˹������������̡��������ı׶��Ǹ߽���������ǳ�����ȡ����ķѼ�������������ң���Щ��������������������еģ���ʹ��ר��Ҳ��һ������ȡ���������������ġ�����ơ�ơ����⡣

��DeepFM���֮ǰ������LR��FM��FFM��FNN��PNN���Լ����ֱ��壺IPNN,OPNN,PNN*��,Wide&Deepģ�ͣ���Щģ����CTR�������Ƽ�ϵͳ�б��㷺ʹ�á�

## 2. ģ���ݽ���ʷ

DeepFM�����Google��wide & deep���������䱾����

1. ��Wide & Deep ���ֵ�wide������ �˹���������+LR ת��ΪFMģ�ͣ��ܿ����˹��������̣�
2. FMģ����deep part����feature embedding��

### 2.1 ����ģ��

�ʼCTR�������Ƽ�ϵͳ����һЩ����ģ��ȡ���˲����Ч�������磺LR��FTRL�� **����ģ��** �и�������ȱ�㣺**�޷���ȡ�߽׵��������**�����Գ��õ���������Ϊ�ļ���**pairwise feature interactions**����ʹ��������������Щ���ֺ��ٻ���û�г��ֵ���������Լ��߽�������������޷���ȡ��

LR����ȱ������޷�����������������˹���������ϣ���Ҳֱ��ʹ��������������ޣ�������ֻ�ܴ������Կɷֻ�������Կɷֵ����⡣

### 2.2 FMģ��

����ģ�Ͳ�ǿ���⣬ֱ�ӵ�����FMģ��Ӧ�˶�������Kaggle�ϴ����������ģ�ȡ���˵�һ���ĳɼ�����FMͨ�������� **latent vector** ���ڻ�����ʾ����������������Ͻ���˵ͽ׺͸߽����������ȡ�����⡣����ʵ��Ӧ���������ڼ��㸴�Ӷȣ�һ��Ҳ��ֻ���ǵ�2�׽���������

�����ֽ����˸Ľ��������FFM��������Field�ĸ��

### 2.3 �������ѧϰ

����DNN��ͼ��������NLP������ȡ��ͻ�ƣ����Ǽ�����ʶ��DNN��������ʾ�ϵ���Ȼ���ơ���������ʹ��CNN��RNN����CTRԤ����ģ�͡����ǣ� **CNNģ�͵�ȱ���ǣ�ƫ����ѧϰ�������������������**  **RNNģ�͵�ȱ���ǣ��Ƚ�������������(ʱ��)��ϵ�����ݡ�**

FNN (Factorization-machine supported Neural Network) �������Ӧ������һ�ηǳ�����ĳ��ԣ���ʹ��Ԥ��ѵ���õ�FM���õ���������Ȼ����ΪDNN��������ѵ��ģ�͡�ȱ�����ڣ�������FMԤѵ����Ч����
��������PNN (Product-based Neural Network)��PNNΪ�˲���߽������������`embedding layer`��`first hidden layer`֮��������һ��`product layer`������product layerʹ���ڻ����������Ϸֱ�������`IPNN, OPNN, PNN*`�������͡�

������FNN����PNN�����Ƕ���һ���Ʋ���ȥ��ȱ�㣺 **���ڵͽ׵����������ѧϰ���ıȽ��١�** ��ǰ������˵�����ͽ���������CTRҲ�Ƿǳ���Ҫ�ġ�

Google��ʶ����������⣬Ϊ��ͬʱѧϰ�ͽ׺͸߽��������������� **Wide&Deepģ��** ���������һ��**����ģ�ͣ�Wide part��**��**Deepģ��(Deep part)**����������ģ����Ҫ��ͬ�����룬��**Wide part**���ֵ����룬����**�����˹��������̡�**

**����** ����Щģ���ձ鶼�����������⣺

1. ƫ������ȡ�ͽ׻��߸߽׵��������������ͬʱ��ȡ���������͵�������
2. ��Ҫרҵ������֪ʶ�����������̡�

DeepFM��Wide&Deep�Ļ����Ͻ��иĽ����ɹ���������������⣬������һЩ�Ľ����� **����/�ŵ�** ���£�


1. ����ҪԤѵ��FM�õ�������
2. ����Ҫ�˹���������
3. ��ͬʱѧϰ�ͽ׺͸߽׵��������
4. FMģ���Deepģ�鹲��Feature Embedding���֣����Ը����ѵ�����Լ�����ȷ��ѵ��ѧϰ



## 3. DeepFM

DeepFM�����ǳ���

��Ҫ�������£�

1.  **FM Component + Deep Component** ��FM��ȡ�ͽ����������Deep��ȡ�߽�������������Ǻ�Wide&Deep��ͬ���ǣ�DeepFM�Ƕ˵��˵�ѵ��������Ҫ�˹��������̡�
2.  **����feature embedding** ��FM��Deep���������`feature embedding`����ʹ��ѵ�����죬����ʹ��ѵ������׼ȷ�����֮�£�Wide&Deep�У�input vector�ǳ�����������˴������˹���Ƶ�pairwise������������������ļ��㸴�Ӷȡ�



**DeepFM�ܹ�ͼ��** 



<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226155639413.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0RieV9mcmVlZG9t,size_16,color_FFFFFF,t_70" width = 60% height = 70%>
</div>



<p align = "center">Figure 1: Wide & deep architecture of DeepFM. The wide and deep component share the same input raw feature vector, which enables DeepFM to learn low- and high-order feature interactions simultaneously from the input raw features.

### 3.1 FM Component

FM���ֵ��������������ɣ�һ�� **Addition Unit** �����**�ڻ���Ԫ**��


$$
y_{FM} = <w,x> + \sum_{j_1 = 1}^{d} \sum_{j_2 = j_1 + 1}^{d} <V_i, V_j>x_{j_1} \cdot x_{j_2}
$$
�����d������one-hot֮���ά�ȣ�����һ���֮Ϊ`feature_size`����Ӧ����one-hot֮ǰ������ά�ȣ����ǳ�֮Ϊ`field_size`��



FM�ܹ�ͼ��



<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226155558504.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0RieV9mcmVlZG9t,size_16,color_FFFFFF,t_70" width = 60% height = 70%>
</div>
<p align = "center">Figure 3: The architecture of DNN

**Addition Unit**  ��ӳ����1�׵�������**�ڻ���Ԫ**��ӳ����2�׵������������Ԥ������Ӱ�졣

**ע�⣺** 
��Ȼ��ʽ��Y_fm�����в��ֶ���ͣ���һ�����������Ǵ�FMģ��ļܹ�ͼ�����ǿ��Կ��������뵽�����Ԫ�Ĳ��ֲ�����һ��������Ӧ����һ��������

ʵ��ʵ���в��õ���FM����֮����ڻ���ʽ�����յ�ά���ǣ�`field_size + embedding_size`����ӦFM Layer�е���Ԫ����: Field���� + Ƕ��ά�� = F + k������ F Ϊone-hot֮ǰ����ά�ȣ�k Ϊembedding������ά�ȣ�

����ֱ�չ��������ά�ȵ�����������ô���ģ��������ģ�ͻ��Ǻ���Ҫ�ģ�

1.  **`field_size` ��Ӧ���� `<W,X>`** ��

   �����X��one-hot֮��ģ�one-hot֮��������ΪX��ÿһ�ж���һ��������ά�ȵ��������������Ǳ�����X��1��������˵���˾��ǵ�������X��ÿ�����������Ƕ�����Ԥ���Ӱ���Ƕ��١��Ƕ����ǣ���W��W��Ӧ�ľ�����Щά��������Ȩ�ء�����one-hot֮������������`feature_size`����ôW��ά�Ⱦ��� `(feature_size, 1)`��

   ����`<W,X>`�ǰ�X��Wÿһ��λ�ö�Ӧ�����ӡ�����X��one-hot֮��ģ����� **�൱��** �ǽ�����һ��**Embedding**��X��W�Ͻ���һ��Ƕ�룬����˵��һ��ѡ��ѡ�����W���У���ʲôѡ���ǣ�����X�в�Ϊ0����Щ������Ӧ��index��ѡ��W�� row=index ���С�

    **���������Embedding** : W��һ������ÿһ�ж�ӦX��һ��ά�ȵ�������������one-hot֮���ά�ȣ�һ��Ҫע�⣩��W������Ϊ1����ʾǶ��֮���ά����1��W��ÿһ�ж�Ӧһ���������൱��������������X_i��Ϊһ��index, X_i������һ��Field i��ֻ��1��Ϊ1������Ķ���0���ĸ�λ�õ�����ֵΪ1����ô��ѡ��W�ж�Ӧ���У���ΪǶ������Field i��Ӧ���µ�������ʾ������ÿһ��Field��ִ�������Ĳ�������ѡ������X_i Embedding֮��ı�ʾ��ע�⵽��ÿ��Field��**�϶���ѡ���ҽ�ѡ��W�е�ĳһ��**(����Ϊʲô��)����ΪW�������ǹ̶��ģ�ÿһ��Field��ѡ��W.cols��Ϊ��Ӧ������������ÿ��Fieldѡ��������ЩW���У�ƴ�������͵õ���X Embedding����µı�ʾ��ά����`num(Field) * num(W.cols)`����Ȼÿ��Field�ĳ��ȿ��ܲ�ͬ�����Ƕ�����W��ѡ��һ�У�����ѡ�����ĳ�������ͬ�ġ���Ҳ��Embedding��һ�����ԣ���Ȼ�����Field���Ȳ�ͬ������Embedding֮��ĳ�������ͬ�ġ�

   ʲô��Embedding��ô���ӣ���ôʵ�ֵģ� **�ǳ��򵥣�ֱ�Ӱ�X��W���ڻ����ɡ�** �ǵģ���û����������ô�򵥣�tensoflow�з�װ���£��ĳ���`tf.nn.embedding_lookup(embeddings, index)`��ԭ����ǲ����˷���ֱ��ѡ����Ӧ���У����Լ�д���������ԣ�`X.shape=(1, feature_size), W.shape = (feture_size, embedding_size)`��֪��Ϊʲô`ѡ��1��ӦW���к����ڻ������һ����`����ô�����ˡ�

   ���ԣ� **FMģ��ͼ�У����߲�����һ��ȫ���ӣ�W���������Ȩ�ء�** ������X��W��˾͵õ������������`Addition Unit`,���ǾͲ������ˣ����ﲢû����ʲô�ӷ����Ͱ��������Ƿ�Ӧ1�������������Ӱ������ˡ�

2.  **`embedding_size`** 

   `embedding_size`��Ӧ����
   $$
   \sum_{j_1 = 1}^{d} \sum_{j_2 = j_1 + 1}^{d} <V_i, V_j>x_{j_1} \cdot x_{j_2}
   $$




   FM�����и����˻����Ĺ�ʽ��
$$
   \sum_{i=1}^{n} \sum_{j=i+1}^{n} {\langle \mathbf{v}_i, \mathbf{v}_j \rangle} x_i x_j \qquad\qquad\qquad\qquad\qquad\qquad(1)\\ 
   =  \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} {\langle \mathbf{v}_i, \mathbf{v}_j \rangle} x_i x_j - \frac{1}{2} \sum_{i=1}^{n} {\langle \mathbf{v}_i, \mathbf{v}_i \rangle} x_i x_i \qquad\qquad\;\;(2)\\ 
   =  \frac{1}{2} \left(\sum_{i=1}^{n} \sum_{j=1}^{n} \sum_{f=1}^{k} v_{i,f} v_{j,f} x_i x_j - \sum_{i=1}^{n} \sum_{f=1}^{k} v_{i,f} v_{i,f} x_i x_i \right) \qquad\,(3) \\ 
   =  \frac{1}{2} \sum_{f=1}^{k} {\left \lgroup \left(\sum_{i=1}^{n} v_{i,f} x_i \right) \cdot \left(\sum_{j=1}^{n} v_{j,f} x_j \right) - \sum_{i=1}^{n} v_{i,f}^2 x_i^2 \right \rgroup} \quad\;\;\,(4) \\ 
   =  \frac{1}{2} \sum_{f=1}^{k}  {\left \lgroup \left(\sum_{i=1}^{n} v_{i,f} x_i \right)^2 - \sum_{i=1}^{n} v_{i,f}^2 x_i^2\right \rgroup} \qquad\qquad\qquad\;\;
$$
   �������Ľ��������[1,K]�ϵ�һ����͡�  **K����W������������Embedding���ά�ȣ�Ҳ����embedding_size** ��Ҳ����˵����DeepFM��FMģ���У����û�жԽ����`[1,K]`������͡����ǰ���K����ƴ�������γ���һ��Kά�ȵ�������

**FM Component�ܽ᣺** 

1. FMģ��ʵ���˶���1�׺�2����������Ľ�ģ��
2. û��ʹ��Ԥѵ��
3. û���˹���������
4. embedding����Ĵ�С�ǣ��������� * Ƕ��ά�ȡ� Ȼ����һ��index��ʾѡ�����ĸ�������

**��Ҫѵ�����������֣�** 


1. input_vector��Addition Unit������ȫ���Ӳ㣬Ҳ����1�׵�Embedding����
2. Sparse Feature��Dense Embedding��Embedding�����м�Ҳ��ȫ���ӵģ�Ҫѵ�������м��Ȩ�ؾ������Ȩ�ؾ���Ҳ����������V��


### 3.2 Deep Component

Deep Component�ܹ�ͼ��

<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226155435645.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0RieV9mcmVlZG9t,size_16,color_FFFFFF,t_70" width = 60% height = 70%>
</div>


<p align = "center">Figure 3: The architecture of DNN.

Deep Component������ѧϰ **�߽��������** �ġ����������ɫ������ȫ���Ӳ㣬������Ҫ������ȥѧϰ��

����CTR���Ƽ�ϵͳ������one-hot֮���ر�ϡ�裬���ֱ�ӷ��뵽DNN�У������ǳ��࣬����û����ô�������ȥѵ������һ�����硣���� **������һ��Embedding�㣬���ڽ���γ�ȡ�** 

**�������������Embedding�㣬�����ص㣺** 

1. ��������ĳ��Ȳ�ͬ������ӳ��󳤶ȶ�����ͬ��.`embedding_size(k)`
2. embedding��Ĳ�����ʵ��ȫ���ӵ�Weights����ͨ���������Լ�ѧϰ���ġ�

Embedding��ļܹ�ͼ��




<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226155400196.png" width = 60% height = 70%>
</div>


embedding layer��ʾΪ��
$$
a^{(0)} = [e_1, e_2, \dots, e_m]
$$
���� <img src="https://latex.codecogs.com/gif.latex?e_i"/> �ǵ� $i$ ��filed��embedding��m��filed������

Ȼ�� <img src="https://latex.codecogs.com/gif.latex?a^{(0)}"/> ���ݸ�deep part��ǰ���������£�
$$
a^{(l+1)} = \sigma(W^{(l)}a^{(l)} + b^{(l)})
$$
���� <img src="https://latex.codecogs.com/gif.latex?l"/> �ǲ���ȣ�<img src="https://latex.codecogs.com/gif.latex?\sigma"/> �Ǽ������ <img src="https://latex.codecogs.com/gif.latex?a^{(l)}"/>, <img src="https://latex.codecogs.com/gif.latex?W^{(l)}"/>, <img src="https://latex.codecogs.com/gif.latex?b^{(l)}"/> �ֱ��ǵ� $l$ ��������Ȩ�غ�ƫ�á�

Ȼ��õ�dense real-value ����ʸ��������͵�sigmoid������CTRԤ�⣺
$$
y_{DNN} = \sigma(W^{|H|+1} \cdot a^{|H|} + b^{|H|+1})
$$
���� <img src="https://latex.codecogs.com/gif.latex?|H|"/> �����ز����



ֵ��ע����ǣ� **FMģ���Deepģ���ǹ���feature embedding�ģ�Ҳ����V����** 

�ô���

1. ģ�Ϳ��Դ���ԭʼ�������У�ͬʱѧϰ�ͽ׺͸߽��������
2. ������Ҫ�˹��������̡�Wide&Deep�еͽ������������ͬ���������̵õ��ġ�

### 3.3 �Ա�����ģ��

ģ��ͼ��


<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226155215938.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0RieV9mcmVlZG9t,size_16,color_FFFFFF,t_70" width = 80% height = 70%>
</div>


<p align = "center">Figure 5: The architectures of existing deep models for CTR prediction: FNN, PNN, Wide & Deep Model

#### 3.3.1 FNN

**FNN is a FM-initialized feedforward neural network.** 
**FNNʹ��Ԥѵ����FM����ʼ��DNN��Ȼ��ֻ��Deep���֣�����ѧϰ�ͽ����������** 

**FNNȱ�㣺** 

1. Embedding�Ĳ�����FM��Ӱ�죬��һ��׼ȷ
2. Ԥѵ���׶������˼��㸴�Ӷȣ�ѵ��Ч�ʵ�
3. FNNֻ��ѧϰ���߽׵����������ģ����û�жԵͽ�������ģ��

#### 3.3.2 PNN

**PNN��Ϊ�˲���߽�������PNN�ڵ�һ�����ز��embedding��֮�䣬������һ��product layer��** 

����product�Ĳ�ͬ������������PNN��IPNN��OPNN��PNN* �ֱ��Ӧ�ڻ�����������߻�ϡ�

����Ϊ�˼ӿ���㣬���ý��Ƽ���ķ����������ڻ���������ڻ�������һЩ��Ԫ���������m*kά��vectorת����kά�ȵ�vector�����������ʧ�˽϶���Ϣ������һ��û���ڻ��ȶ���

�����ڻ��ļ��㸴�Ӷ����ɷǳ��ߣ�ԭ���ǣ�product layer�������Ҫ�͵�һ�����ز����ȫ���ӵġ�

**PNNȱ�㣺** 

1. �ڻ�������㸴�Ӷȸߡ����ý��Ƽ���ķ������û���ڻ��ȶ���
2. product layer�������Ҫ���һ�����ز�ȫ���ӣ����¼��㸴�ӶȾӸ߲���
3. ��FNNһ����ֻ��ѧϰ���߽׵�������ϡ�û�ж���1�׺�2���������н�ģ��

#### 3.3.3 Wide&Deep

**Wide & Deep��Ƶĳ�������ͬʱѧϰ�ͽ׺͸߽��������������wide������Ҫ����֪ʶ�����������̡�** 

Wide���ֿ�����LR���滻�������Ļ��ͺ�DeepFM����ˡ�
����DeepFM����feature embedding �������ʹ���ڷ��򴫲���ʱ��ģ��ѧϰfeature embedding�������ֻ���ǰ�򴫲���ʱ��Ӱ��ͽ׺͸߽�������ѧϰ����ʹ��ѧϰ���ӵ�׼ȷ��

**Wide&Deepȱ�㣺** 

1. ��Ҫ����������ȡ�ͽ��������

**Note:** 

��ʵ�ϣ������Ѿ���ȷָ����DeepFM����� Wide & Deep �Ĵ��µ㣺

1. ��Wide & Deep ���ֵ�wide������ �˹���������+LR ת��ΪFMģ�ͣ��ܿ����˹��������̣�
2. FMģ����deep part����feature embedding��

����֮������feature embedding��ʹ��embedding�����õ��˺ܺõı�������ģ��������ϸ��

#### 3.3.4 DeepFM

**�ŵ㣺** 

1. û����FMȥԤѵ��������V������Vȥ��ʼ�������硣�����֮��FNN����ҪԤѵ��FM����ʼ��DNN��
2. FMģ�鲻�Ƕ����ģ��Ǹ�����ģ��һ��ѵ��ѧϰ�õ��ġ������֮��Wide&Deep�е�Wide��Deep������û�й���ģ�
3. ����Ҫ�������̡������֮��Wide&Deep�е�Wide������Ҫ�������̣�
4. ѵ��Ч�ʸߡ������PNNû����ô�������

�ܽ���ǣ�

1. û��Ԥѵ����no pre-training��
2. ����Feature Embedding��û���������̣�no feature engineering��
3. ͬʱѧϰ�ͽ׺͸߽����������capture both low-high-order interaction features��



����ģ�ͶԱ�ͼ���£�


<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226155135590.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0RieV9mcmVlZG9t,size_16,color_FFFFFF,t_70" width = 70% height = 70%>
</div>




## 4. ʵ��

### 4.1 ʵ��׼��

#### 4.1.1 ���ݼ�

1) Criteo Dataset

2) Company* Dataset

#### 4.1.2 ����ָ��

1) AUC (Area Under ROC) 

2) Logloss (cross entropy).

#### 4.1.3 ģ�ͱȽ�

һ���Ƚ�9��ģ�ͣ�LR, FM, FNN, PNN (three variants), Wide & Deep, and DeepFM

����Ϊ�˱ܿ� Wide & Deepģ����wide���ֵ��������̹���������LR & DNN and FM & DNN���д��档

#### 4.1.4 ��������

To evaluate the models on Criteo dataset, we follow the parameter settings in [Qu et al., 2016] for FNN and PNN: 

(1)dropout: 0.5;

(2) network structure: 400-400-400; 

(3) optimizer: Adam; 

(4) activation function: tanh for IPNN, relu for
other deep models. 

To be fair, our proposed DeepFM uses the same setting. The optimizers of LR and FM are FTRL and Adam respectively, and the latent dimension of FM is 10.


#### 4.1.5 ��������

**Efficiency Comparison** 

We compare the efficiency of different models on Criteo dataset by the following formula:

<img src="https://latex.codecogs.com/gif.latex?\frac{training\time\of\deep\CTRmodel}{training\time\of\LR}"/>




<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226155013548.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0RieV9mcmVlZG9t,size_16,color_FFFFFF,t_70" width = 80% height = 70%>
</div>

<p align = "center">Figure 6: Time comparison.



DeepFM���������ݼ��ϼ����ﵽ����õı��֡�

1) pre-training of FNN makes it less efficient; 

2) Although the speed up of IPNN and PNN* on GPU is higher than the other models, they are still computationally expensive because of the inefficient inner product operations; 

3) The DeepFM achieves almost the most efficient in both tests.

**Effectiveness Comparison** 

ʱ�������±�



<div align = center>
<img src = "https://img-blog.csdnimg.cn/20181226154846920.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0RieV9mcmVlZG9t,size_16,color_FFFFFF,t_70" width = 60% height = 70%>
</div>



ʵ����ۣ�

1. ���������ѧϰ�����CTRԤ��ģ�͵����ܣ�
2. ��ȷ��ͬʱѧϰ�ͽ׺͸߽����������ͬ���������CTRԤ�������ܣ�
3. ��ѧϰ�ͽ׺͸߽��������ʱ��ʹ����ͬ��feature embedding�������CTR���ܡ�

### 4.2 ����������

�����л�������һЩ������ʵ������ֱ�Ӹ������ۣ����ʵ�ֵ�ʱ����Բο��¡�

| ������     | ����                            | ��ע                                 |
| ---------- | ------------------------------- | ------------------------------------ |
| �����   | 1. IPNNʹ��tanh 2. ����ʹ��ReLU |                                      |
| ѧϰ����   | Adam                            |                                      |
| Dropout    | 0.6\~0.9                         |                                      |
| ���ز����� | 3\~5                             | ����ʵ�����ݴ�С����                 |
| ��Ԫ���� | 200\~600                         | ����ʵ�����ݴ�С����                 |
| ������״   | constant                        | һ�������֣��̶����������½������Ρ� |

PS: constantЧ����ã��������ز�ÿһ�����Ԫ������ **��ͬ** ��

�ⲿ��ʵ��ͼƬ̫�࣬��ֱ�Ӳο�ԭ���ġ�

## 5. Note

����һ������CTRԤ�����Ƽ�ϵͳ������Ҫ����ѧϰ���û������Ϊ����������������ϡ��ڲ�ͬ���Ƽ������У��ͽ�����������߸߽�����������ܶ�������յ�CTR����Ӱ�졣

���ӷֽ��(Factorization Machines, FM)ͨ������ÿһά�������������ڻ�����ȡ������ϡ����յĽ��Ҳ�ǳ��á����ǣ���Ȼ����������FM���ԶԸ߽�������Ͻ��н�ģ����ʵ������Ϊ���㸴�Ӷȵ�ԭ��һ�㶼ֻ�õ��˶���������ϡ�

��ô���ڸ߽׵����������˵�����Ǻ���Ȼ���뷨��ͨ�����������缴DNNȥ�����

> �����ͼƬ�������ſ��ֽ�����AI�������ʹ�õ�PPT��

����֮ǰҲ���ܹ��ˣ�������ɢ�����Ĵ�������ʹ�õ��ǽ�����ת����Ϊone-hot����ʽ�����ǽ�One-hot���͵��������뵽DNN�У��ᵼ���������̫�ࣺ

<div align = center>
<img src = "https://upload-images.jianshu.io/upload_images/4155986-f4363ca2be689dbb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" width = 80% height = 80%>
</div>


��ν����������أ�������FFM�е�˼�룬��������Ϊ��ͬ��field��

<div align = center>
<img src = "https://upload-images.jianshu.io/upload_images/4155986-5f476d2c5b616232.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" width = 80% height = 80%>
</div>


<div align = center>
<img src = "https://upload-images.jianshu.io/upload_images/4155986-12f3119df69b7b5b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" width = 70% height = 70%>
</div>



���ǵͽ׺͸߽�����������������������ز��У��������ϣ���ѵͽ�������ϵ�����ģ��Ȼ���ںϸ߽�������ϡ�


<div align = center>
<img src = "https://upload-images.jianshu.io/upload_images/4155986-7e036f56982d323b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" width = 80% height = 80%>
</div>

����DNN��FM����һ��������ںϣ�

<div align = center>
<img src = "https://upload-images.jianshu.io/upload_images/4155986-2b8d2e22017ad339.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" width = 80% height = 80%>
</div>


���ߵ��ں��ܵ���˵��������ʽ��һ�� **���нṹ** ������**���нṹ**��


<div align = center>
<img src = "https://upload-images.jianshu.io/upload_images/4155986-cd51e0bd97ab285d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" width = 60% height = 80%>
</div>


<div align = center>
<img src = "https://upload-images.jianshu.io/upload_images/4155986-1118724d47e2c65e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700" width = 60% height = 80%>
</div>

���нṹ������FNN�� **DeepFM���ǲ��нṹ�е�һ�ֵ��ʹ���** 


## �ο�����

[1] [DeepFM: A Factorization-Machine based Neural Network for CTR Prediction](https://www.ijcai.org/proceedings/2017/0239.pdf)

[2] [�Ƽ�ϵͳ�������ѧϰ(��)--DeepFMģ�����ۺ�ʵ��](https://ask.hellobi.com/blog/wenwen/11840)

[3] [������CTRԤ��ϵ��(һ)�CDeepFM����](https://blog.csdn.net/u010352603/article/details/80201033)

[4][CTRԤ��ר�� | һ�ĸ㶮DeepFM��������ʵ��](https://xueqiu.com/9217191040/110099109)
