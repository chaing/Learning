study opencv...
==============

> [OpenCV](http://www.opencv.org/) 的全称是Open Source Computer Vision Library，是一个跨平台的计算机视觉库。OpenCV是由英特尔公司发起并参与开发，以BSD许可证授权发行，可以在商业和研究领域中免费使用。OpenCV可用于开发实时的图像处理、计算机视觉以及模式识别程序。该程序库也可以使用英特尔公司的IPP进行加速处理。

读取文件
----

    Mat image = imread( argv[1] ,CV_LOAD_IMAGE_GRAYSCALE);

or:

    IplImage * image;
    image=cvLoadImage(argv[1],-1);

存储文件
----

    imwrite(const string& , image);

缩放
----

    int width = image.cols;
    int height = image.rows;
    double dst_size = 200.0;
    double scale = dst_size/max(width,height);
    Size dsize = Size(width*scale,height*scale);
    Mat image2 = Mat(dsize,CV_32S);
    resize(image, image2, dsize);

特征点检查器
----

    int minHessian = 480;
    Ptr<FeatureDetector> detector = Ptr<FeatureDetector>(new SurfFeatureDetector(minHessian));
    vector<KeyPoint> kp;
    detector->detect( image, kp );

描述子
----

    #define DESCRIPTOR_TYPE "SURF" // SURF,SIFT,BRIEF,
    Mat dp;
    Ptr<DescriptorExtractor> de = DescriptorExtractor::create( DESCRIPTOR_TYPE );//描述子
    de->compute( image, kp, dp );

查找匹配点
----

    #define MATCHER_TYPE "FlannBased"    // BruteForce,FlannBased,BruteForce-L1,...
    Ptr<DescriptorMatcher> matcher = DescriptorMatcher::create( MATCHER_TYPE );
    vector< vector<DMatch> > matches;
    matcher->knnMatch( dpL, dpR, matches, 2 ); // L:query, R:train

转换
----

Mat类型侧重于计算，数学性较高，openCV对Mat类型的计算也进行了优化。而CvMat和IplImage类型更侧重于“图像”，openCV对其中的图像操作（缩放、单通道提取、图像阈值操作等）进行了优化。

    - Mat -> IplImage

        IplImage pImg= IplImage(imgMat);    // 假设Mat类型的imgMat图像数据存在



    - IplImage -> Mat

        Mat img(pImg,0);    // 0是不复制

行列转换
----

    cv:Mat mat;
    int rows = mat.rows;
    int cols = mat.cols;

    cv::Size s = mat.size();
    rows = s.height;
    cols = s.width;

END,GOOD LUCK!
--------------