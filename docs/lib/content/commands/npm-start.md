mport React, { useState } from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import { View, Text, TouchableOpacity, StyleSheet } from 'react-native';

const Stack = createNativeStackNavigator();

function HomeScreen({ navigation }) {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>MY GPS TO MY PTS</Text>
      <Text style={styles.subtitle}>No Uber. No Lyft. You drive.</Text>
      
      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Map')}>
        <Text style={styles.buttonText}>🗺️ OPEN MAP</Text>
      </TouchableOpacity>

      <TouchableOpacity style={[styles.button, { backgroundColor: '#ff2d55' }]} onPress={() => navigation.navigate('Emergency')}>
        <Text style={styles.buttonText}>🚨 EMERGENCY PULL OVER</Text>
      </TouchableOpacity>
    </View>
  );
}

function MapScreen() {
  const = useState(2450);
  return (
    <View style={styles.container}>
      <Text style={styles.header}>📍 LIVE GPS MAP</Text>
      <Text style={{ fontSize: 90, marginVertical: 30 }}>🚚</Text>
      <Text style={{ color: '#00ff9d', fontSize: 24 }}>Classic Atlanta Work Truck</Text>
      <Text style={{ color: 'white', marginTop: 20 }}>Current Road: Anxiety Lane</Text>
      <Text style={{ color: '#00ff9d', marginTop: 10 }}>{points} GPS Points</Text>
    </View>
  );
}

function EmergencyScreen() {
  return (
    <View style={[styles.container, { backgroundColor: '#220000' }]}>
      <Text style={{ color: '#ff2d55', fontSize: 36, fontWeight: 'bold', textAlign: 'center' }}>
        PULL OVER NOW
      </Text>
      <TouchableOpacity style={styles.bigRedButton}>
        <Text style={{ color: 'white', fontSize: 24, fontWeight: 'bold' }}>📞 CALL 988</Text>
      </TouchableOpacity>
      <Text style={{ color: 'white', textAlign: 'center', marginTop: 30 }}>
        You are not alone.
      </Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1, backgroundColor: '#0a0a0a', justifyContent: 'center', padding: 20 },
  title: { color: '#00ff9d', fontSize: 32, fontWeight: 'bold', textAlign: 'center' },
  subtitle: { color: 'white', textAlign: 'center', marginBottom: 40 },
  button: { backgroundColor: '#00ff9d', padding: 18, borderRadius: 16, marginVertical: 10 },
  buttonText: { textAlign: 'center', fontWeight: 'bold', fontSize: 18 },
  bigRedButton: { backgroundColor: '#ff2d55', padding: 25, borderRadius: 16, marginTop: 40 }
});

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator screenOptions={{ headerShown: false }}>
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Map" component={MapScreen} />
        <Stack.Screen name="Emergency" component={EmergencyScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}--
