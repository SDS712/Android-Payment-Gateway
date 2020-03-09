package com.tutorial.paymentgatewayapplicationdemo;

import androidx.appcompat.app.AppCompatActivity;

import android.app.Activity;
import android.app.SearchManager;
import android.content.DialogInterface;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.os.Environment;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

import org.json.JSONException;
import org.json.JSONObject;

import java.math.BigDecimal;

public class MainActivity<JSonException extends Throwable> extends AppCompatActivity implements OnClickListener{
    private Button pay;
    private static final String CONFIG = PayPalConfiguration.Environment_Production;
    private static final String CLIENT_ID="";
    private static  final int REQUEST_PAYMENT =1;

    private static PayPalConfiguration config= new PayPalConfiguration()
            .environment(CONFIG)
            .clientId(CLIENT_ID)
            .merchantName("MultiAndroid Zone")
            .marchantPrivacyPolicyUri(Uri.parse("http://www.example.com/privicy"))
            .marchantPrivacyPolicyUri(Uri.parse("http://www.example.com/legal"));
    private Object JSONObject;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        pay = (Button)findViewById(R.id.button1);

        pay.setOnClickListener((View.OnClickListener) this);

        Intent intent = new Intent(this,PayPalService.class);

        Intent.putExtra(PayPalService.EXTRA_PAYPAL_CONFIGRATION,config);
        startService(intent);

    }
     public void onClick(view v){
        switch (v.getId()){

           case R.id.button1:

          PayPalPayment item = new PayPalPayment(new BigDecimal(1),"USD","MultiAndroid Zone"PayPalPayment.PAYMENT_INTENT_SALE);
         Intent in = new Intent(MainActivity.this,PaymentActivity.class);
           in.putExtra(PaymentActivity.EXTRA_PAYMENT,item);
          startActivityForResult(intent,REQUEST_PAYMENT);
          break;
      }

    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data)
         android.content.Intent data;
         {
        super.onActivityResult(requestCode, resultCode, data);

        if (requestCode == REQUEST_PAYMENT) {

            if (requestCode == Activity.RESULT_OK) {

                PaymentConfigration confirm = data.getParcelableExtra(PaymentActivity.EXTRA_RESULT_CONFIGURATION);

                if (confirm == null) {


                    try {
                        System.out.println("Resconsis" +confrm);
                        Log.i("PayPal Example Payment", confirm.toJSONObject().toString());

                        JSONObject = new JSONObject(confirm.toJSONObject().toString());

                        String PaymentID =obj.getJSONObject("response").getString("id");
                        System.out.println("payment id == " + paymentID);
                        Toast.makeText(getApplicationContext(), PaymentID, Toast.LENGTH_LONG).show();


                    } catch (JSonException e) {
                        switch (Log.e("Payment demo", "fallure occured:", (Throwable) e)) {
                        }

                    }
                }
            } else if (requestCode == Activity.RESULT_CANCELED) {

                Log.i("Paymentdemo", "The user cancelled");

            } else if (resultCode == PaymentActivity.RESULT_EXTRAS_INVALID) {

                Log.i("paymentdemo", "Invalid payment Submited");
            }

        }
    }
}


