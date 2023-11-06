package com.example.good_pet;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;


public class Tela_inicio extends AppCompatActivity implements Runnable{

    Thread thread;
    Handler handler;
    int i;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.tela_inicio);

        handler = new Handler();
        thread = new Thread(this);
        thread.start();

    }

    @Override
    public void run() {

        i = 1;
        try{
            while(i<100){
                Thread.sleep(12);
                handler.post(new Runnable() {
                    @Override
                    public void run() {
                        i++;
                    }
                });
            }
        }catch (Exception e){

        }
        startActivity(new Intent(this, Tela_log.class));
    }
}
