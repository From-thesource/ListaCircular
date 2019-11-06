# ListaEstática

#include<iostream>
#define maxtam 4
using namespace std;



struct lista {
        int vet[maxtam];
        int tam;
        int primeiro;
        int ultimo;
};

char menu() {
    char c;
    cout << "\nopcoes: " <<endl;
    cout << "i: inserir" <<endl;
    cout << "m: mostrar" << endl;
    cout << "p: insere p=0"<<endl;
    cout << "q: insere na posição desejada"<<endl;
    cout << "e: exclui." << endl;
    cout << "s: sair"<<endl;
    cout << "\nEntre com sua opcao: ";
    cin >> c;
    return c;
}
int main(){

        lista l;
        char op ='N';
        l.tam=0;
        l.primeiro=0;
        l.ultimo=0;
        op = menu();
        while(op!='s') {
            switch (op){

            case 'i':
            case 'I':

                if(l.tam == 0){
                        l.primeiro = 0;
                        l.ultimo = 0;
                        cout << "Entre com o numero: " << endl;
                        cin >> ws >> l.vet[0];
                        l.tam=1;
                } else if(l.tam<maxtam){
                        cout << "Entre com o numero: " << endl;
                        cin >> ws >> l.vet[l.tam];
                        l.ultimo = (l.ultimo+1)%maxtam;
                        l.tam++;
                } else {
                        cout << "Erro ao inserir, lista cheia!" << endl;
                }
                break;
            case 'm':
            case 'M':
                for(int i=0; i<maxtam; i++){
                    if(i!=0)
                        cout << ' ';
                        cout << l.vet[i];
                } cout << endl;
                break;
            case 'p':
            case 'P':
                if (l.tam<maxtam){
                    for(int i=l.tam;i>0;i--){
                        l.vet[i] = l.vet[i-1];
                    }
                    cout << "Entre com o numero: " << endl;
                    cin >> ws >> l.vet[0];
                    l.tam++;
                } else {
                    cout << "Erro ao inserir!Lista cheia." << endl;
                }
                break;
            case 'q':
            case 'Q':
                if(l.tam<maxtam){
                        int pos;
                        do {
                            cout << "Entre com a posicao: " << endl;
                            cin >> l.vet[pos-1];
                            l.tam++;
                        } while (pos<1||pos>>(l.tam+1));
                        for(int i=l.tam;i>(pos-1);i++){
                            l.vet[i-1];
                        }
                        cout << "Entre com o numero: " << endl;
                        cin >> l.vet[pos-1];
                        l.tam++;
                } else {
                        cout << "Erro ao inserir! Lista cheia. " << endl;
                }
                break;
            case 'e':
            case 'E':
                 if(l.tam>0) {
                    int pos;
                    do {
                        cout<< "Entre com a posicao: [1.." <<l.tam<<"]: ";
                        cin>>ws>>pos;
                    } while(pos <1 || pos>(l.tam));
                    for(int i=(pos);i<l.tam;i++){
                        l.vet[i-1]=l.vet[i];
                    }
                    l.tam--;
                }
                break;
            default:
                cout << "opcao invalida!" << endl;
            }
            op = menu();


        }

        return 0;
}
