# ReactNative_lsitApp
FlatList, and its data property &amp; renderItem func

demo

![Flatlist](https://raw.githubusercontent.com/QueenieCplusplus/ReactNative_listApp/master/demo_for_list.png)

list.js

    import * as React from 'react';
    import { Text, View, StyleSheet, FlatList, Image, Button} from 'react-native';
    import TouchHistoryMath from 'react-native/Libraries/Interaction/TouchHistoryMath';

    export default class ListCompo extends React.Component {


      constructor(props){
        super(props);
        this.state = {
          data: [
            {key: "W Hotel"},
            {key: "Marriot Hotel"},
            {key: "Le Meridien"}
          ],
          pressed: false
        }
      }

      showItem = data => {
        return(
        <Text>{data.item.key}</Text>
        )
      }

      clickHander = () => {
        this.setState({pressed: true})
      }

      render(){

        return (
          <View style={styles.container}>
            <Text style={styles.paragraph}>
               A List for Hotels
            </Text>

            <br/>
            <Image style={styles.logo} source={require('../assets/hotel.png')} />

            <br/>
            <Button color = "#c92c98" title= 'show me hotels' size={10} onPress = {this.clickHandler}/>

            <br/>

            <FlatList

              data={this.state.data}
              renderItem = {this.showItem}>

            </FlatList>

          </View>
        );


      }

    }


    const styles = StyleSheet.create({
      container: {
        alignItems: 'center',
        justifyContent: 'center',
        padding: 24,
      },
      paragraph: {
        color: "#c92c98",
        margin: 24,
        marginTop: 0,
        fontSize: 22,
        fontWeight: 'bold',
        textAlign: 'center',
      },
      logo: {
        height: 128,
        width: 128,
      }
    });


App.js


        import * as React from 'react';
        import { Text, View, StyleSheet } from 'react-native';
        import Constants from 'expo-constants';

        // You can import from local files
        import ListCompo from './components/list';

        // or any pure javascript modules available in npm
        import { Card } from 'react-native-paper';

        export default function App() {
          return (
            <View style={styles.container}>
              <Text style={styles.paragraph}>
              </Text>
              <Card>
                <ListCompo />
              </Card>
            </View>
          );
        }

        const styles = StyleSheet.create({
          container: {
            flex: 1,
            justifyContent: 'center',
            paddingTop: Constants.statusBarHeight,
            backgroundColor: '#ecf0f1',
            padding: 8,
          },
          paragraph: {
            margin: 24,
            fontSize: 18,
            fontWeight: 'bold',
            textAlign: 'center',
          },
        });

