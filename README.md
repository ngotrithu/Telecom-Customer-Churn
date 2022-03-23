# Telecom-Customer-Churn
## Mô tả:
- Trong ngành viễn thông, khách hàng có thể lựa chọn từ nhiều nhà cung cấp dịch vụ khác nhau và chủ động chuyển đổi từ nhà cung cấp dịch vụ này sang nhà cung cấp khác một cách dễ dàng và không có nhiều sự ràng buộc.
- Việc giữ chân từng khách hàng cá nhân rất khó khăn vì hầu hết các công ty đều có một lượng khách hàng lớn và không thể dành nhiều thời gian cho từng KH một được
- Tuy nhiên, nếu một công ty có thể dự báo những khách hàng nào có khả năng rời bỏ sớm, thì công ty đó có thể tập trung vào tập KH này từ đấy chăm sóc tốt hơn hoặc tung ra nhiều chương trình ưu đãi tốt hơn

=> Mục đích giữ chân KH, tăng độ phủ sóng, thu hút thêm sự trung thành của KH.

- Tỷ lệ Customer Churn là một chỉ số quan trọng vì việc giữ chân khách hàng hiện nay ít tốn kém hơn nhiều so với việc tìm kiếm một KH mới
- Để giảm bớt tình trạng rời bỏ của khách hàng, các công ty viễn thông cần dự đoán những khách hàng nào có nguy cơ rời bỏ cao
- Càng có nhiều khách hàng trong mạng lưới của mình, chi phí ban đầu càng thấp và lợi nhuận càng lớn. Do đó, Customer Churn là một yếu tố vô cùng quan trọng quyết định đến sự thành công của một công ty, một doanh nghiệp.
## Mục đích:
- Với dữ liệu đầu vào, dự báo xem liệu KH có rời bỏ sản phẩm dịch vụ của công ty hay không?
## Techniques:
- Exploratory Data Analysis (EDA)
- Preprocessing Data
- Feature Scaling
- Handle Imbalanced Dataset SMOTE()
- Build 9 Models
- Fine Tuning Hyperparameters (GridSearchCV, RandomizedSearchCV, Optuna)
- Another Approach with Pipeline
## Modeling:
- LogisticRegression
- Decision Tree
- Bagging Classifier
- SVM
- RandomForest
- XGBoost
- LightGBM
- AdaBoost
- VotingClassifier
## Model Selection
<a href="https://drive.google.com/uc?export=view&id=1mJyBTJG3M8jsp3TT9wUDZbJCGfo3dn7Q"><img src="https://drive.google.com/uc?export=view&id=1mJyBTJG3M8jsp3TT9wUDZbJCGfo3dn7Q" style="width: 500px; max-width: 100%; height: auto" title="Click for the larger version." /></a>
- Mô hình VotingClassifier cho tỷ lệ dự đoán chính xác cao nhất 78.56%. Tuy nhiên để tuning hyperparameters nhằm cải thiện thêm độ chính xác cho mô hình chúng ta có thể tiến hành cho các mô hình khác như LightGBM và RF
## Fine tuning
<a href="https://drive.google.com/uc?export=view&id=1eXr_HAENd2voLh1O3iZGFnoVbVIJEOAY"><img src="https://drive.google.com/uc?export=view&id=1eXr_HAENd2voLh1O3iZGFnoVbVIJEOAY" style="width: 500px; max-width: 100%; height: auto" title="Accuracy after Fine tuning" /></a>
- Với bài toán Customer Churn, chúng ta nên chú trọng vào việc giảm số lượng sai lầm loại I (FP) mà mô hình phán đoán được. Những khách hàng thuộc sai lầm loại I về thực tế họ đã rời bỏ và ngưng sử dụng các sản phẩm, dịch vụ của công ty để chuyển sang sử dụng sản phẩm, dịch vụ của công ty khác nhưng mô hình dự đoán những khách hàng này chưa rời bỏ (VD: Khách hàng của Viettel đã chuyển sang đăng ký các gói viễn thông khác như Vinaphone, Mobiphone nhưng mô hình dự đoán họ vẫn đang sử dụng dịch vụ của Viettel). Điều dẫn đến một sự lãng phí lớn cho công ty khi chúng ta tung ra các chương trình khuyến mại, ưu đãi dành riêng cho những đối tượng KH này nhằm mục đích giữ chân họ.
- Nên ngoài việc lựa chọn mô hình tốt, chúng ta cũng cần lựa chọn những mô hình có các TH thuộc sai lầm loại I là thấp nhất.
- Dựa vào độ chính xác và confusion matrix của các mô hình đã sử dụng ở trên thì những hyperparameter của mô hình LightGBM của kết quả Optuna đáp ứng hai yêu cầu trên, nên chúng ta sẽ chọn mô hình này làm mô hình cuối cùng để áp dụng vào bài toán Customer Churn.
