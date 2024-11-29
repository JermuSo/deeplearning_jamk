## Tuloksia mallin eri parametreilla

### Ensimmäinen "vakio"
```
model = Sequential([
    Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
    Dense(64, activation='relu'),
    Dense(32, activation='relu'),
    Dense(1)
])

model.compile(optimizer='adam', loss='mse', metrics=['mae'])

early_stopping = EarlyStopping(
    monitor='val_loss',
    patience=10,
    restore_best_weights=True
)

history = model.fit(
    X_train, y_train,
    epochs=50,
    batch_size=32,
    validation_split=0.2,
    verbose=1,
    callbacks=[early_stopping]

Test Loss (MSE): 1.2359148263931274
est MAE: 0.8650335073471069
```
### Dropout 

```
model = Sequential([
    Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dropout(0.2),
    Dense(32, activation='relu'),
    Dense(1)
])

# Määritellään mallin optimointiparametrit
model.compile(optimizer=Adam(learning_rate=0.001), loss='mse', metrics=['mae'])

# Koulutetaan malli
early_stopping = EarlyStopping(
    monitor='val_loss',
    patience=10,
    restore_best_weights=True
)

history = model.fit(
    X_train, y_train,
    epochs=50,
    batch_size=32,
    validation_split=0.2,
    verbose=1,
    callbacks=[early_stopping]
)

Test Loss (MSE): 1.158100962638855
Test MAE: 0.8310815691947937

```

### Dynaaminen oppimisnopeus ja takaisin 100 epoch

```
# Määritellään malli
model = Sequential([
    Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dropout(0.2),
    Dense(32, activation='relu'),
    Dense(1)
])

# Määritellään mallin optimointiparametrit
model.compile(optimizer=Adam(learning_rate=0.001), loss='mse', metrics=['mae'])

# Koulutetaan malli
early_stopping = EarlyStopping(
    monitor='val_loss',
    patience=10,
    restore_best_weights=True
)

lr_scheduler = ReduceLROnPlateau(
    monitor='val_loss',
    factor=0.5,  # pienennetään oppimisnopeutta puoleen
    patience=5,  # odotetaan 5 epokkia ennen kuin oppimisnopeutta pienennetään
    min_lr=1e-6
)

history = model.fit(
    X_train, y_train,
    epochs=100,
    batch_size=32,
    validation_split=0.2,
    verbose=1,
    callbacks=[early_stopping, lr_scheduler]
)

# Mallin suorituskyvyn arviointi testidatalla
test_loss, test_mae = model.evaluate(X_test, y_test)

print(f'Test Loss (MSE): {test_loss}')
print(f'Test MAE: {test_mae}')

# Ennusteet testidatalla
predictions = model.predict(X_test)

#predictions = np.expm1(predictions)

19365/19365 [==============================] - 14s 721us/step - loss: 1.0296 - mae: 0.7791 - val_loss: 0.9943 - val_mae: 0.7690 - lr: 1.5625e-05
Epoch 99/100
19365/19365 [==============================] - 14s 724us/step - loss: 1.0287 - mae: 0.7789 - val_loss: 1.0020 - val_mae: 0.7735 - lr: 1.5625e-05
Epoch 100/100
19365/19365 [==============================] - 14s 728us/step - loss: 1.0271 - mae: 0.7778 - val_loss: 0.9997 - val_mae: 0.7715 - lr: 1.5625e-05
6052/6052 [==============================] - 2s 397us/step - loss: 0.9915 - mae: 0.7703
Test Loss (MSE): 0.9914945960044861
Test MAE: 0.7702962756156921
6052/6052 [==============================] - 2s 343us/step
```

### 200 epoch paras 12.11. 21.00

```

# Määritellään malli
model = Sequential([
    Dense(128, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dropout(0.2),
    Dense(32, activation='relu'),
    Dense(1)
])

# Määritellään mallin optimointiparametrit
model.compile(optimizer=Adam(learning_rate=0.001), loss='mse', metrics=['mae'])

# Koulutetaan malli
early_stopping = EarlyStopping(
    monitor='val_loss',
    patience=10,
    restore_best_weights=True
)

lr_scheduler = ReduceLROnPlateau(
    monitor='val_loss',
    factor=0.5,  # pienennetään oppimisnopeutta puoleen
    patience=5,  # odotetaan 5 epokkia ennen kuin oppimisnopeutta pienennetään
    min_lr=1e-6
)

history = model.fit(
    X_train, y_train,
    epochs=200,
    batch_size=32,
    validation_split=0.2,
    verbose=0,
    callbacks=[early_stopping, lr_scheduler]
)

# Mallin suorituskyvyn arviointi testidatalla
test_loss, test_mae = model.evaluate(X_test, y_test)

print(f'Test Loss (MSE): {test_loss}')
print(f'Test MAE: {test_mae}')

# Ennusteet testidatalla
predictions = model.predict(X_test)

#predictions = np.expm1(predictions)

Epoch 145/200
19365/19365 [==============================] - 14s 748us/step - loss: 1.0225 - mae: 0.7769 - val_loss: 0.9806 - val_mae: 0.7614 - lr: 3.9063e-06
Epoch 146/200
19365/19365 [==============================] - 14s 745us/step - loss: 1.0232 - mae: 0.7770 - val_loss: 0.9818 - val_mae: 0.7619 - lr: 3.9063e-06
6052/6052 [==============================] - 2s 400us/step - loss: 0.9710 - mae: 0.7590
Test Loss (MSE): 0.9709531664848328
Test MAE: 0.7589946389198303
6052/6052 [==============================] - 2s 350us/step
```

### 200k tasoitettu

```
Epoch 123/200
3873/3873 [==============================] - 3s 733us/step - loss: 1.1443 - mae: 0.8282 - val_loss: 1.1107 - val_mae: 0.8178 - lr: 1.0000e-06
Epoch 124/200
3873/3873 [==============================] - 3s 735us/step - loss: 1.1456 - mae: 0.8281 - val_loss: 1.1109 - val_mae: 0.8181 - lr: 1.0000e-06
1211/1211 [==============================] - 0s 393us/step - loss: 1.1255 - mae: 0.8252
Test Loss (MSE): 1.1255130767822266
Test MAE: 0.8252246975898743
1211/1211 [==============================] - 0s 353us/step
```

### 29.11
```
model = Sequential([
    Dense(256, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.3),
    Dense(128, activation='relu'),
    Dropout(0.3),
    Dense(64, activation='relu'),
    Dense(32, activation='relu'),
    Dense(1)
])
Epoch 86/100
17379/17379 [==============================] - 18s 1ms/step - loss: 0.4350 - mae: 0.8003 - val_loss: 0.4201 - val_mae: 0.7823 - lr: 1.2901e-07
5431/5431 [==============================] - 2s 424us/step - loss: 0.4200 - mae: 0.7827
Test Loss (MSE): 0.419969767332077
Test MAE: 0.7826929092407227
5431/5431 [==============================] - 2s 337us/step
```
```
Epoch 68/100
14317/14317 [==============================] - 14s 977us/step - loss: 0.3796 - mae: 0.7370 - val_loss: 0.3691 - val_mae: 0.7248 - lr: 8.5950e-07
Epoch 69/100
14317/14317 [==============================] - 14s 976us/step - loss: 0.3795 - mae: 0.7371 - val_loss: 0.3693 - val_mae: 0.7249 - lr: 7.7355e-07
Epoch 70/100
14317/14317 [==============================] - 14s 975us/step - loss: 0.3794 - mae: 0.7371 - val_loss: 0.3686 - val_mae: 0.7243 - lr: 6.9620e-07
4474/4474 [==============================] - 2s 440us/step - loss: 0.3693 - mae: 0.7250
Test Loss (MSE): 0.3693493902683258
Test MAE: 0.724952220916748
4474/4474 [==============================] - 2s 368us/step
```


