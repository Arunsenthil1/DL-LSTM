# DL- Developing a Deep Learning Model for NER using LSTM

## AIM
To develop an LSTM-based model for recognizing the named entities in the text.

## Problem Statement and Dataset
An organization needs to extract important information such as names of people, locations, organizations, and other entities from large amounts of unstructured text data. Manually identifying these named entities is time-consuming and inefficient. To automate this process, a model based on Long Short-Term Memory (LSTM) networks will be developed. LSTM is a type of recurrent neural network that is capable of capturing long-term dependencies in sequential data, making it suitable for natural language processing tasks. The model will be trained on labeled text data where each word is tagged with its corresponding entity type. By learning the context and relationships between words in a sentence, the model can accurately identify and classify named entities. After training, the model will be tested on new, unseen text to evaluate its performance in recognizing entities. The objective is to achieve high accuracy in extracting relevant information from text data efficiently.


<img width="541" height="698" alt="image" src="https://github.com/user-attachments/assets/84a339d9-27b7-45a0-9c15-76a022f24b99" />


## DESIGN STEPS
### STEP 1:
Collect Dataset – Obtain a labeled dataset for Named Entity Recognition (NER).

Write your own steps

### STEP 2: 
Preprocess Data – Tokenize text, convert words to numbers, and pad sequences.


### STEP 3: 
Word Embedding – Convert words into vector representations using an embedding layer.

### STEP 4: 
Build Model – Create an LSTM-based deep learning model.



### STEP 5: 
Train Model – Train the model using the training dataset.


### STEP 6: 
Evaluate Model – Test the model and measure accuracy.





## PROGRAM

### Name: Arun S

### Register Number: 212224230023

```python
# Model definition
class BiLSTMTagger(nn.Module):
    def __init__(self, vocab_size,tagset_size, embedding_dim=50, hidden_dim=100):
        super(BiLSTMTagger,self).__init__()
        self.embedding=nn.Embedding(vocab_size,embedding_dim)
        self.dropout=nn.Dropout(0.1)
        self.lstm=nn.LSTM(embedding_dim,hidden_dim,batch_first=True,bidirectional=True)
        self.fc=nn.Linear(hidden_dim*2,tagset_size)
    def forward(self, input_ids):
        x.self.embedding(x)
        x=self.dropout(x)
        x, _ = self.lstm(x)
        return self.fc(x)

model =BiLSTMTagger(len(word2idx)+1,len(tag2idx)).to(device)
loss_fn =nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)


# Training and Evaluation Functions
def train_model(model, train_loader, test_loader, loss_fn, optimizer, epochs=3):
    def train_model(model, train_loader, test_loader, loss_fn, optimizer, epochs=3):
    train_losses, val_losses = [], []
    for epoch in range(epochs):
        model.train()
        train_loss = 0.0
        for batch in train_loader:
            input_ids = batch["input_ids"].to(device)
            labels = batch["labels"].to(device)
            optimizer.zero_grad()
            outputs = model(input_ids) 
            loss = loss_fn(outputs.view(-1, len(tag2idx)), labels.view(-1))
            loss.backward()
            optimizer.step()
            train_loss += loss.item()
        train_losses.append(total_loss)

        model.eval()
        val_loss=0
        with torch.no_grad():
            for batch in test_loader:
              input_ids = batch["input_ids"].to(device)
              labels = batch["labels"].to(device)
              outputs = model(input_ids)
              loss = loss_fn(outputs.view(-1, len(tag2idx)), labels.view(-1))
              val_loss += loss.item()
        val_losses.append(val_loss)
        print(f"Epoch {epoch+1}: Train loss = {total_loss:.4f}")
    return train_losses, val_losses


```

### OUTPUT


## Loss Vs Epoch Plot

<img width="658" height="67" alt="image" src="https://github.com/user-attachments/assets/4706f1a5-9370-46d7-8d03-e215d3bba47c" />
<img width="771" height="507" alt="image" src="https://github.com/user-attachments/assets/7861cf2c-ff68-4b58-ab88-d97680189d5b" />


### Sample Text Prediction
<img width="455" height="474" alt="image" src="https://github.com/user-attachments/assets/0714cb6d-6af3-4fbb-8abc-1920dc957988" />


## RESULT
The LSTM-based deep learning model successfully identified named entities such as person, location, and organization from text data with good accuracy.
