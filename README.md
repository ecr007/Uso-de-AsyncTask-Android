# Uso-de-AsyncTask-Android

  ```java
    private class AsyncLoginUser extends AsyncTask<String1, String, String> {

        @Override
        protected void onPreExecute() {
            loading.setVisibility(View.VISIBLE);
        }

        @Override
        protected String doInBackground(String1... params) {

            // Logica del negocio

            // Login WS
            DataFetcherV3 request = new DataFetcherV3();
            String res  = request.checkForLogin(params[0],params[1]);

            Log.d("AE RES","Respuesta doInBackground ->>> "+res);

            return res;
        }

        @Override
        protected void onPostExecute(String result) {
            btnIngresar.setEnabled(true);
            loading.setVisibility(View.INVISIBLE);

            Log.d("AE RES","Respuesta onPostExecute ->>> "+result);
        }
    }
    
    /** Exec  **/
    new AsyncLoginUser().execute(user,pass);
    
